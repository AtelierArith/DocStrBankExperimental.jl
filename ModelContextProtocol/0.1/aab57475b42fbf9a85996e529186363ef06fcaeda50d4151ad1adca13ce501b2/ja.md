```
JSONRPCNotification(; method::String, 
                   params::Union{RequestParams,Dict{String,Any}}) <: Notification
```

応答を期待しないJSON-RPC通知メッセージ。

# フィールド

  * `method::String`: 通知メソッドの名前
  * `params::Union{RequestParams,Dict{String,Any}}`: 通知のためのパラメータ
