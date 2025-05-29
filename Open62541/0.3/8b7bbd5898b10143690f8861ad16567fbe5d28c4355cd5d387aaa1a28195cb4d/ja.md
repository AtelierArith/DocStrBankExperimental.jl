```
response::Ptr{UA_SetMonitoringModeResponse} = UA_Client_MonitoredItems_setMonitoringMode(client::Ptr{UA_Client}, 
    request::Ptr{UA_SetMonitoringModeRequest})
```

は、クライアントAPIを使用して監視対象アイテムの監視モードを設定します。レスポンスのメモリはCによって割り当てられ、使用後は`UA_SetMonitoringModeResponse_delete(response)`を使用してクリーンアップする必要があります。

参照：

[OPC Foundationの監視対象アイテムモデル](https://reference.opcfoundation.org/Core/Part4/v105/docs/5.12.1)

[OPC Foundationの監視モード](https://reference.opcfoundation.org/Core/Part4/v105/docs/5.12.1.3)

[`UA_SetMonitoringModeRequest`](@ref)

[`UA_SetMonitoringModeResponse`](@ref)
