```
UA_Client_sendAsyncReadRequest(client::Ptr{UA_Client}, 
    request::Ptr{UA_ReadRequest},
    readCallback::UA_ClientAsyncReadCallback,
    userdata::Ptr{Cvoid}, requestId::UInt32)::UA_StatusCode
```

は非同期クライアントAPIを使用して読み取りリクエストを送信します。

参照：

[`UA_ReadRequest`](@ref)

[`UA_ClientAsyncReadCallback_generate`](@ref)
