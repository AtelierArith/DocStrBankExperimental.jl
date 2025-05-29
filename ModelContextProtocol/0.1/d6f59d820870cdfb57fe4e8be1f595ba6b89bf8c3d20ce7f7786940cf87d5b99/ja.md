```
JSONRPCResponse(; id::RequestId, result::Union{ResponseResult,Dict{String,Any}}) <: Response
```

成功したリクエストに対して返されるJSON-RPCレスポンスメッセージ。

# フィールド

  * `id::RequestId`: このレスポンスが対応するリクエストに一致する識別子
  * `result::Union{ResponseResult,Dict{String,Any}}`: メソッド実行の結果
