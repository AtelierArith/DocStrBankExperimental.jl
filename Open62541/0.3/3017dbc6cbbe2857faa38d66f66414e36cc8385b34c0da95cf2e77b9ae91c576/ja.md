```
UA_Client_MonitoredItems_setMonitoringMode_async(client::Ptr{UA_Client}, 
    request::Ptr{UA_SetMonitoringModeRequest},
    callback::UA_ClientAsyncServiceCallback,
    userdata::Ptr{Cvoid}, requestId::UInt32)::UA_StatusCode
```

は、監視対象アイテムの監視モードを設定するために非同期クライアントAPIを使用します。

参照：

[OPC Foundationの監視対象アイテムモデル](https://reference.opcfoundation.org/Core/Part4/v105/docs/5.12.1)

[OPC Foundationの監視モード](https://reference.opcfoundation.org/Core/Part4/v105/docs/5.12.1.3)

[`UA_SetMonitoringModeRequest`](@ref)

[`UA_ClientAsyncServiceCallback_generate`](@ref)
