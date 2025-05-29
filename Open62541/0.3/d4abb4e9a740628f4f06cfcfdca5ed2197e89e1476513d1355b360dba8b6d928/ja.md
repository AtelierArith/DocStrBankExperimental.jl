```
response::Ptr{UA_SetPublishingModeResponse} = UA_Client_Subscriptions_setPublishingMode(client::Ptr{UA_Client}, 
    request::Ptr{UA_SetPublishingModeRequest}) 
```

は、クライアントAPIを使用してサブスクリプションの発行モードを設定します。レスポンスのメモリはCによって割り当てられ、使用後は`UA_SetPublishingModeResponse_delete(response)`を使用してクリーンアップする必要があります。

参照：

[OPC Foundationのサブスクリプションモデル](https://reference.opcfoundation.org/Core/Part4/v105/docs/5.13.1)

[OPC FoundationのSetPublishingMode](https://reference.opcfoundation.org/Core/Part4/v105/docs/5.13.4)

[`UA_SetPublishingModeRequest`](@ref)

[`UA_SetPublishingModeResponse`](@ref)
