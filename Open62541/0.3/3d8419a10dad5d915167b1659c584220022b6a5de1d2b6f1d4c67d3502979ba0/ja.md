```
UA_ClientAsyncServiceCallback_generate(f::Function)
```

は `UA_ClientAsyncServiceCallback` オブジェクトを作成します。

`f` は次のシグネチャを持つJulia関数でなければなりません: `f(client::Ptr{UA_Client}, userdata::Ptr{Cvoid}, requestId::UInt32, response::Ptr{Cvoid}))::Nothing`
