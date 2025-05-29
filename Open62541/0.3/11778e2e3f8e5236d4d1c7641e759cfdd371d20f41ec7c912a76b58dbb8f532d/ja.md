```
JUA_Client_writeValueAttribute(server::JUA_Client, nodeId::JUA_NodeId, newvalue)::UA_StatusCode
```

は、`client`が接続されているサーバーの`nodeId`に値`newvalue`を書き込むためにクライアントAPIを使用します。

`new_value`は、`JUA_Variant`であるか、またはそのコンストラクタのいずれかと互換性のあるJuliaの値/配列でなければなりません。

参照してください [`JUA_Variant`](@ref)
