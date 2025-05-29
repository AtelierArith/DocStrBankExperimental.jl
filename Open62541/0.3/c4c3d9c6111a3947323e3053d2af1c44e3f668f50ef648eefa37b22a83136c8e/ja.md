```julia
struct UA_SetPublishingModeRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `publishingEnabled::Bool`
  * `subscriptionIdsSize::UInt64`
  * `subscriptionIds::Ptr{UInt32}`
