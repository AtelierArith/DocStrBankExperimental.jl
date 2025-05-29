```
UA_ClientAsyncReadCallback_generate(f::Function)
```

は `UA_ClientAsyncReadCallback` オブジェクトを作成します。

`f` は次のシグネチャを持つJulia関数でなければなりません: `f(client::Ptr{UA_Client}, userdata::Ptr{Cvoid}, requestId::UInt32, readresponse::Ptr{UA_ReadResponse}))::Nothing`
