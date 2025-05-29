Kucoin.subscribe(ws*client, topic[, id[, is*private*channel[, return*response]]]) -> nothing

サーバーにサブスクリプションメッセージを送信します。詳細については、Kucoinの公式[docs](https://docs.kucoin.com/#subscribe)を参照してください。

# 引数

  * `ws_client::WebSocketClient`: ウェブソケットクライアント
  * `topic::String`: サブスクライブしたいトピック
  * `id::String`: [オプション] リクエストを識別するためのユニークな文字列で、ackのidプロパティと同じです。
  * `is_private_channel::Bool`: [オプション] 特定のトピック（例：`/market/level2`）の場合、

`is_private_channel`が利用可能です。`is_private_channel`がtrueに設定されている場合、ユーザーはそのトピックに関連する自分自身に関するメッセージのみを受信します。

  * `return_response::Bool`: [オプション] trueに設定されている場合、kucoinは成功したサブスクリプション後に

確認メッセージを返します。
