```
JSONRPCRequest(; id::RequestId, method::String, 
             params::Union{RequestParams, Nothing}, 
             meta::RequestMeta=RequestMeta()) <: Request
```

サーバー上のメソッドを呼び出すために使用されるJSON-RPCリクエストメッセージ。

# フィールド

  * `id::RequestId`: リクエストの一意の識別子
  * `method::String`: 呼び出すメソッドの名前
  * `params::Union{RequestParams, Nothing}`: メソッドのためのパラメータ
  * `meta::RequestMeta`: リクエストのための追加メタデータ
