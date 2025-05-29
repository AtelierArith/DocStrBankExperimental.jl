```
dcc_logoutbutton(;kwargs...)
```

ログアウトボタンコンポーネントは、`logout_url`プロパティにフォームのポストリクエストを送信するためのログアウトボタンです。使用はdash-deployment-server認証を意図しています。

DDSの使用法:

`dcc.LogoutButton(logout_url=os.getenv('DASH_LOGOUT_URL'))`

カスタム使用法:

  * ログインメカニズムを実装します。
  * ポストメソッドハンドラを持つflaskルートを作成します。

`@app.server.route('/logout', methods=['POST'])`

  * ログアウトルートは、ユーザーがログアウトするために必要な処理を行うべきです。
  * セッションをクッキーに保存している場合は、クッキーをクリアします:

`rep = flask.Response(); rep.set_cookie('session', '', expires=0)`

  * ログアウトボタンコンポーネントを作成し、logout_urlを割り当てます。

`dcc.LogoutButton(logout_url='/logout')`

詳細なドキュメントと例については、https://dash.plotly.com/dash-core-components/logout_button を参照してください。

  * `id` (文字列; オプション): ボタンのID。
  * `className` (文字列; オプション): ボタンのCSSクラス。
  * `label` (文字列; オプション): ボタンのテキスト
  * `loading_state` (要素を含むリスト is*loading, prop*name, component*name   - `is*loading`(ブール; オプション): コンポーネントが読み込まれているかどうかを決定します   -`prop*name`(文字列; オプション): どのプロパティが読み込まれているかを保持します   -`component*name` (文字列; オプション): 読み込まれているコンポーネントの名前を保持します; オプション): dash-rendererから来る読み込み状態オブジェクトを保持するオブジェクト
  * `logout_url` (文字列; オプション): ポストログアウトリクエストを送信するためのURL。
  * `method` (文字列; オプション): ログアウトフォームを送信するためのHTTPメソッド。
  * `style` (辞書; オプション): ボタンのスタイル
