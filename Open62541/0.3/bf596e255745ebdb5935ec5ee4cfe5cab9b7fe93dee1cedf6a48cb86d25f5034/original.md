```julia
struct UA_DeleteSubscriptionsRequest
```

Fields:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `subscriptionIdsSize::UInt64`
  * `subscriptionIds::Ptr{UInt32}`
