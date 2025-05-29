```
dcc_confirmdialogprovider(;kwargs...)
dcc_confirmdialogprovider(children::Any, kwargs...)
dcc_confirmdialogprovider(children_maker::Function, kwargs...)
```

ConfirmDialogProviderコンポーネント 子コンポーネントがクリックされたときに確認ダイアログを表示するラッパーコンポーネントです。

例えば：

```
dcc.ConfirmDialogProvider(
    html.Button('click me', id='btn'),
    message='Danger - Are you sure you want to continue.'
    id='confirm')
```

  * `children` (Bool | Real | String | Dict | Array; optional): クリックをハイジャックしてポップアップを表示する子要素。
  * `id` (String; optional): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。IDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `cancel_n_clicks` (optional): ポップアップがキャンセルされた回数。
  * `cancel_n_clicks_timestamp` (optional): 最後にキャンセルボタンがクリックされた時間。
  * `displayed` (Bool; optional): モーダルが現在表示されているかどうか。
  * `loading_state` (要素を含むリスト is*loading, prop*name, component*name   - `is*loading`(Bool; optional): コンポーネントが読み込み中かどうかを判断します   -`prop*name`(String; optional): どのプロパティが読み込み中かを保持します   -`component*name` (String; optional): 読み込み中のコンポーネントの名前を保持します; optional): dash-rendererからの読み込み状態オブジェクトを保持するオブジェクト
  * `message` (String; optional): ポップアップに表示するメッセージ。
  * `submit_n_clicks` (optional): 送信がクリックされた回数
  * `submit_n_clicks_timestamp` (optional): 最後に送信ボタンがクリックされた時間。
