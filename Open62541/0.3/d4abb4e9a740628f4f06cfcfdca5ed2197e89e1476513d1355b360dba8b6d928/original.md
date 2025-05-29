```
response::Ptr{UA_SetPublishingModeResponse} = UA_Client_Subscriptions_setPublishingMode(client::Ptr{UA_Client}, 
    request::Ptr{UA_SetPublishingModeRequest}) 
```

uses the client API to set the publishing mode on subscriptions. Note that memory for the response is allocated by C and needs to be cleaned up using `UA_SetPublishingModeResponse_delete(response)` after its use.

See also:

[Subscription model at OPC Foundation](https://reference.opcfoundation.org/Core/Part4/v105/docs/5.13.1)

[SetPublishingMode at OPC Foundation](https://reference.opcfoundation.org/Core/Part4/v105/docs/5.13.4)

[`UA_SetPublishingModeRequest`](@ref)

[`UA_SetPublishingModeResponse`](@ref)
