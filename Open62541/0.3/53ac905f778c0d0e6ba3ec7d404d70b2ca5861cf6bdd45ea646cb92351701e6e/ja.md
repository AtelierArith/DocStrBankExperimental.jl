```
JUA_Server_writeValue(server::JUA_Server, nodeId::JUA_NodeId, newvalue)::UA_StatusCode
```

は、サーバーAPIを使用して、`server`上の`nodeId`に値`newvalue`を書き込みます。`new_value`は、`JUA_Variant`であるか、またはそのコンストラクタのいずれかと互換性のあるJuliaの値/配列でなければなりません。

参照してください [`JUA_Variant`](@ref)
