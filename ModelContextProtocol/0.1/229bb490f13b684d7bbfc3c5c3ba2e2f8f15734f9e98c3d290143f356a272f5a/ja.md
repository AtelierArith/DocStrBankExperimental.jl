```
parse_message(json::String) -> MCPMessage
```

JSON-RPCメッセージ文字列を適切な型のメッセージオブジェクトに解析します。

# 引数

  * `json::String`: 生のJSON-RPCメッセージ文字列

# 戻り値

  * `MCPMessage`: 型付きのMCPMessageサブタイプ（JSONRPCRequest、JSONRPCResponse、JSONRPCNotification、またはJSONRPCError）
