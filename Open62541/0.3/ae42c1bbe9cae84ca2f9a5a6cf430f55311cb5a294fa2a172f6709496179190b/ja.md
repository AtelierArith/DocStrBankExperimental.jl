```
UA_ClientAsyncBrowseCallback_generate(f::Function)
```

は `UA_ClientAsyncBrowseCallback` オブジェクトを作成します。

`f` は次のシグネチャを持つJulia関数でなければなりません: `f(client::Ptr{UA_Client}, userdata::Ptr{Cvoid}, requestId::UInt32, writeresponse::Ptr{UA_WriteResponse}))::Nothing`
