```
WSClient
```

Chrome DevTools Protocol 通信のための WebSocket クライアント。

# フィールド

  * `ws::Union{WebSocket, Nothing}`: WebSocket 接続、または接続されていない場合は何もない
  * `ws_url::String`: 接続するための WebSocket URL
  * `is_connected::Bool`: 接続状態フラグ
  * `message_channel::Channel{Dict{String, Any}}`: メッセージ通信のためのチャネル
  * `next_id::Int`: メッセージ ID のカウンター
  * `page_loaded::Bool`: ページの読み込みが完了したかどうかを示すフラグ
  * `endpoint::String`: デバッグエンドポイントの URL
