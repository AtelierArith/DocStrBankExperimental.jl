```
UA_Client_MonitoredItems_setTriggering_async(client::Ptr{UA_Client}, 
    request::Ptr{UA_SetTriggeringRequest},
    callback::UA_ClientAsyncServiceCallback,
    userdata::Ptr{Cvoid}, requestId::UInt32)::UA_StatusCode
```

は、非同期クライアントAPIを使用して、監視項目のトリガーを設定します。

参照：

[OPC Foundationの監視項目モデル](https://reference.opcfoundation.org/Core/Part4/v105/docs/5.12.1)

[OPC Foundationの監視モード](https://reference.opcfoundation.org/Core/Part4/v105/docs/5.12.1.3)

[`UA_SetTriggeringRequest`](@ref)

[`UA_ClientAsyncServiceCallback_generate`](@ref)
