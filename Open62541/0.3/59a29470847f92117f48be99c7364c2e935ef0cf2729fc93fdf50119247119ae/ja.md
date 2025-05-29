```
output::Union{Any, Tuple{Any, ...}} = JUA_Client_call(client::JUA_Client, 
    parentnodeid::JUA_NodeId, methodid::JUA_NodeId, inputs::Union{Any, Tuple{Any, ...}})
```

は、`client`が接続されているサーバー上のメソッドノード（`methodid`）を呼び出すためにクライアントAPIを使用します。`inputs`は単一の引数または引数のタプルのいずれかである可能性があります。呼び出されるメソッドに応じて、適切な出力または出力引数のタプルが返されます。
