```julia
struct UA_TransferSubscriptionsRequest
```

Fields:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `subscriptionIdsSize::UInt64`
  * `subscriptionIds::Ptr{UInt32}`
  * `sendInitialValues::Bool`
