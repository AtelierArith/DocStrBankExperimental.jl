```
serialize_message(msg::MCPMessage) -> String
```

MCPメッセージオブジェクトをJSON-RPC準拠の文字列にシリアライズします。

# 引数

  * `msg::MCPMessage`: シリアライズするメッセージオブジェクト（リクエスト、レスポンス、通知、またはエラー）

# 戻り値

  * `String`: JSON-RPC 2.0仕様に従ったメッセージのJSON文字列表現
