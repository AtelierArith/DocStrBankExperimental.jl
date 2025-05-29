```
dcc_confirmdialog(;kwargs...)
```

ConfirmDialogコンポーネントは、オプションのメッセージと2つのボタン（「OK」と「キャンセル」）を持つブラウザのネイティブ「確認」モーダルを表示するために使用されます。このConfirmDialogは、ユーザーが追加の確認ステップを必要とするアクションを実行しているときにボタンと一緒に使用できます。

  * `id` (String; optional): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。IDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `cancel_n_clicks` (optional): ポップアップがキャンセルされた回数。
  * `cancel_n_clicks_timestamp` (optional): 最後にキャンセルボタンがクリックされた時間。
  * `displayed` (Bool; optional): ConfirmDialogを送信するためにtrueに設定します。
  * `message` (String; optional): ポップアップに表示するメッセージ。
  * `submit_n_clicks` (optional): 提出ボタンがクリックされた回数。
  * `submit_n_clicks_timestamp` (optional): 最後に提出ボタンがクリックされた時間。
