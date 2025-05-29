```julia
struct UA_SetTriggeringRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `subscriptionId::UInt32`
  * `triggeringItemId::UInt32`
  * `linksToAddSize::UInt64`
  * `linksToAdd::Ptr{UInt32}`
  * `linksToRemoveSize::UInt64`
  * `linksToRemove::Ptr{UInt32}`
