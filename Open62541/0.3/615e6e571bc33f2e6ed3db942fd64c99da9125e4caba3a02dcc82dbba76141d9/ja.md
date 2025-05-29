```
UA_Client_sendAsyncWriteRequest(client::Ptr{UA_Client}, 
    request::Ptr{UA_WriteRequest},
    readCallback::UA_ClientAsyncWriteCallback,
    userdata::Ptr{Cvoid}, requestId::UInt32)::UA_StatusCode
```

は非同期クライアントAPIを使用して書き込みリクエストを送信します。

参照：

[`UA_WriteRequest`](@ref)

[`UA_ClientAsyncWriteCallback_generate`](@ref)
