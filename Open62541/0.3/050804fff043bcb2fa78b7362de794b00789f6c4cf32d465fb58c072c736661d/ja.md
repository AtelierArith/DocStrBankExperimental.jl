```
UA_Client_call_async(client::Ptr{UA_Client}, objectId::Ptr{UA_NodeId}, methodId::Ptr{UA_NodeId},
    inputSize::Csize_t, input::Ptr{UA_Variant}, callback::UA_ClientAsyncCallCallback, 
    userdata::Ptr{Cvoid}, requestId::UInt32)::UA_StatusCode
```

は、クライアントが接続しているサーバー上のメソッド `methodId` を呼び出すために非同期クライアントAPIを使用します。

参照: [`UA_ClientAsyncCallCallback_generate`](@ref)
