```
response::Ptr{UA_SetTriggeringResponse} = UA_Client_MonitoredItems_setTriggering(client::Ptr{UA_Client}, 
    request::Ptr{UA_SetTriggeringRequest}) 
```

は、クライアントAPIを使用して監視項目の監視モードを設定します。レスポンスのメモリはCによって割り当てられ、使用後は`UA_SetTriggeringResponse_delete(response)`を使用してクリーンアップする必要があります。

参照：

[OPC Foundationの監視項目モデル](https://reference.opcfoundation.org/Core/Part4/v105/docs/5.12.1)

[OPC FoundationのSetTriggering](https://reference.opcfoundation.org/Core/Part4/v105/docs/5.12.5)

[`UA_SetTriggeringRequest`](@ref)

[`UA_SetTriggeringResponse`](@ref)
