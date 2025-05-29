```
result::Union{Any, Tuple{Any, ...}} = JUA_Server_call(server::JUA_Server, request::JUA_CallMethodRequest)
```

は、`server` 上のメソッド呼び出しリクエスト `request` を処理するためにサーバーAPIを使用します。`result` は呼び出されたメソッドによって生成された出力です。これは通常、数値または文字列（またはその配列）です。メソッドが複数の出力を生成する場合、それらはタプルとして返されます。

```
result::Union{Any, Tuple{Any, ...}} = JUA_Server_call(server::JUA_Server, objectid::JUA_NodeId, 
    methodid::JUA_NodeId, inputarg)
```

内部で `JUA_CallMethodRequest` を作成する、さらに高レベルのメソッドです。クライアント側の `JUA_Client_call` に相当します。

参照：

  * [`JUA_CallMethodRequest`](@ref)
  * [`JUA_Client_call`](@ref)
