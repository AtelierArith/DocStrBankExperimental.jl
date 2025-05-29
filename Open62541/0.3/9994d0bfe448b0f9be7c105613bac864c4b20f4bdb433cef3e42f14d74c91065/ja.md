```
UA_Client_sendAsyncBrowseRequest(client::Ptr{UA_Client}, 
    request::Ptr{UA_BrowseRequest},
    readCallback::UA_ClientAsyncBrowseCallback,
    userdata::Ptr{Cvoid}, requestId::UInt32)::UA_StatusCode
```

は非同期クライアントAPIを使用してブラウズリクエストを送信します。

参照：

[`UA_BrowseRequest`](@ref)

[`UA_ClientAsyncBrowseCallback_generate`](@ref)
