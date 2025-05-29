```
UA_ClientAsyncCallCallback_generate(f::Function)
```

は `UA_ClientAsyncCallCallback` オブジェクトを作成します。

`f` は次のシグネチャを持つJulia関数でなければなりません: `f(client::Ptr{UA_Client}, userdata::Ptr{Cvoid}, requestId::UInt32, callresponse::Ptr{UA_CallResponse}))::Nothing`
