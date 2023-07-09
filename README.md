# <映画レビュー>

## サイト概要
### サイトテーマ
映画の特徴をタグとして登録しそのタグ等を参照することで気になる映画を検索したり、
視聴が可能なコンテンツを確認できるレビューサイト

### テーマを選んだ理由
私は映画が好きなのだが、明るい作品が観たい、激しいアクションものが観たい等観たい作品の特徴はあるが、
特にはっきりと見たい作品があるわけではないという状況に直面することがあり、
その時特徴から映画を探すことはできないかと考えたことがあったこと、
また、特定の見たい作品があったとして、近年ではサブスクリプションを視聴媒体として用いることが多く、
その作品はどこかのサービスで配信が行われているのかを一目で確認したいと思う機会があったことから、
これらの需要を満たす
・作品の特徴をタグとして設定できるようにする
・作品を配信しているサービスを確認できるようにする
上記二つの機能を実装したレビューサイトがあればよいと思い、このテーマにした

### ターゲットユーザ
映画が好きな人

### 主な利用シーン
特徴から映画を検索する、映画が視聴可能なサービスを確認する、及び映画のレビュー登録・閲覧する

## 開発環境
- OS：Linux(CentOS)
- 言語：HTML,CSS,JavaScript,Ruby,SQL
- フレームワーク：Ruby on Rails
- JSライブラリ：jQuery
- IDE：Cloud9

## 使用方法
TMDBに登録されている映画の情報を閲覧することが可能。
また、キーワードや映画のジャンルから映画を検索することも可能。
ログインしたユーザーは映画のレビューを投稿することが可能。
管理者権限でログインすることによって、ユーザーやレビューの管理が可能。

 - 映画情報の閲覧方法（ログイン不要）
 1. ヘッダーのメニューバーの[映画]のボタンをクリックして映画一覧（Movies/index）に移動する。
 2. 情報を閲覧したい映画のタイトルを入力
 3. 映画のタイトルをクリックすることで映画の情報を見る画面（Movies/show）に移動できる。
 
 - アカウントの新規登録方法
 1. ヘッダーのメニューバーの[新規登録]ボタンをクリックしてアカウント新規登録画面（/users/sign_up）に移動する。
 2. eメールアドレスとパスワード、会員名をフォームに入力する。
 　  この際、eメールアドレスは@マークを中に埋め込んだ形（例'：a@b'など）でなければならず、パスワードは6文字以上でなければならない。
 3. [Sign_up]ボタンをクリックすることで会員登録が完了する。失敗した場合はエラーメッセージの指示に従って入力を修正すること。
 
 - ログイン方法
 1. ヘッダーのメニューバーの[ログイン]ボタンをクリックする
 2. 登録されているeメールアドレスとパスワードをフォームに入力する
 3. [sign_in]ボタンをクリックすることでログインができる。

 - レビューの投稿方法（要ログイン）
 1. レビューを投稿したい映画の映画の詳細画面（Movies/show）で〚レビューを投稿する〛ボタンをクリックする
 2. レビューの入力フォーム画面（reviews/new）が表示されるので、レビューの内容（レビューのタイトル、1～5段階の評価、本文）を入力する。
 3. 黄色い[投稿]ボタンをクリックすることでレビューの投稿が完了する。
 4. 作成したレビューは詳細画面（reviews/show）の[編集]ボタンをクリックすることで編集フォーム（reviews/edit）に移動することができる。
 5. また、投稿前に[下書きに保存]をクリックすることで、非公開の状態でレビューを保存することができる。
 6. 下書きは編集フォーム（reviews/edit）の[下書きを公開]ボタンをクリックすることで公開することができる。

 - 管理者権限でのログイン方法
　ユーザーやレビューを管理できる管理者権限でのログイン方法。 
　1. /admin/sign_in にアドレスを手動で入力してアクセスする。
　2. Emailの入力欄に 'admin@test',パスワードの入力欄に '000000' をそれぞれ入力する。
　3. [Log in]ボタンをクリックすれば管理者権限でログインできる。

 - 
　

 ## ページの見方
 - メニューバー
 ヘッダーにメニューバーを設置している。
 [Movie Review] トップ画面（homes/top）へのリンク。
 [映画]映画一覧（movies）へのリンク。
 [レビュー]レビュー一覧画面（reviews）へのリンク。
 [新規登録]非ログイン時のみ表示される。会員登録画面（users/sign_up）へのリンク。
 [ログイン]非ログイン時のみ表示される。ログイン画面（users/sign_in）へのリンク。
 [マイページ]一般会員でのログイン時のみ表示される。マイページ（user）へのリンク。
 [ログアウト]ログイン時のみ表示される。ログアウト処理を行い、トップ画面へ移動する。
 [ユーザー] 管理者権限でのログイン時のみ表示される。ユーザー一覧画面（admin/users）へのリンク。
 
 - homes/top
   - トップ画面。ログインしていない状態だとゲストログイン用のボタンが表示され、クリックすることで閲覧用のゲストアカウントでログインできる。
   - 
   
 - movies
   - 映画一覧画面。映画を検索することができる。
   - 管理者権限でログインしている状態(アドレスにadminが付いている)でも仕様に変更はない。
 
 - movies/show
   - 映画詳細情報画面。映画の情報（タイトル、ジャンル、配信しているサブスクリプションサービス）を確認できる。
   - 映画のジャンルはTMDBに基づいてカテゴライズされたものであり、クリックすることで同じジャンルの映画を検索できる。
   - その映画のレビューも一覧で確認できる。
   - [レビューを投稿する]ボタンをクリックすることでその映画のレビューの投稿フォーム画面に移動できる。
   - 管理者権限でログインした（アドレスにadminが付いている）時はレビューを投稿できない。
  
 - reviews
 　- レビューの一覧画面。レビューの検索ができる。
 　- レビュータイトルをクリックすることでレビューの詳細画面（review/）に移動できる。
 　- 投稿者名をクリックすることで同じ投稿者のレビューを検索できる。
 　- 映画タイトルをクリックすることで映画の詳細画面に移動できる。
 
 - review/
 　- レビューの詳細情報画面。レビューの詳細な情報（タイトル、投稿者、映画、評価）を確認できる。
 　- コメントを書き込むことが可能。フォームにコメントの内容を書き込んで真下の[投稿]ボタンをクリックすることで投稿できる。
 　- レビューの投稿者はレビューの編集と削除のリンクが表示される。
 
 - reviews/new
 　- レビュー投稿画面。タイトル、評価、本文を入力できる。
 　- 評価はjQuery Raty（https://github.com/wbotelhos/raty）を利用した、星五つによる評価。
 　- [投稿]ボタンをクリックすることで投稿できる。その際、空欄があれば投稿に失敗する。
 　- [下書きを保存]ボタンをクリックすることで非公開の状態でレビューを保存できる。こちらの場合は空欄があっても保存は可能。
 
 - reviews//edit
 　- レビューの編集画面。レビューのタイトル、評価、本文を修正できる。
 　- [投稿を更新]ボタンをクリックすることで投稿されている情報を更新できる。
 
 - users/sign_in
   - ユーザーの新規登録画面。
   - eメールアドレス、パスワード（確認のために2箇所）、ユーザー名を入力して[Sign_up]ボタンをクリックすることでユーザー登録できる。
  
 - users/sign_in
   - ユーザーログイン画面。
   - 登録されているeメールアドレス、パスワードを入力して[Sign_in]ボタンをクリックすることでログインできる。
   
 - user
 　- マイページ。現在ログインしているアカウントの情報（名前、メールアドレス、投稿したレビュー）を閲覧できる。
 
 - admin/sign_in
   - 管理者権限でのログイン専用ページ。リンクを設定したボタンを用意していないため、移動するためには手動でアドレスを入力する必要がある。
   - eメールアドレス（admin@test）、パスワード（000000）を入力して、[Sign_in]ボタンをクリックすることでログインできる。
 
 - admin/users
 　- ユーザー一覧画面。すべてのユーザーの ID,名前,メールアドレス,ステータス（退会して会員機能が無効になっているかどうかの状態）を確認できる。
 　- ユーザーの名前をクリックすることで、クリックしたユーザーの管理者権限における詳細画面（admin/users/）に移動できる。

 - admin/users/
 　- 管理者権限におけるユーザーの詳細画面。ID,名前,メールアドレス,ステータス,これまでに登校したレビューが確認できる。
 　- 会員ステータスの欄の下に[退会]もしくは[有効]ボタンが設置されており、これをクリックすることで表示されている会員の退会ステータスを変更できる。
  
## 使用素材
- 外部サービスの画像素材・音声素材を使用した場合は、必ずサービス名とURLを明記してください。
- 使用しない場合は、使用素材の項目をREADMEから削除してください。

API(TMDB：https://www.themoviedb.org) で取得した情報・画像を利用する>
