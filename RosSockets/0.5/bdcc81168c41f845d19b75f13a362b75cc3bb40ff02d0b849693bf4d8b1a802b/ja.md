```
send(connection::Connection, msg::String)
```

メッセージを送信します。

# 引数

  * `connection`: `open_connection` から取得した `Connection`。
  * `msg`: 送信するメッセージ。注意: 一部のTCPサーバーでは、メッセージが特定の形式（例えばJSON）でフォーマットされている必要があり、メッセージを終了するために `\n` のような改行文字が必要な場合があります。
