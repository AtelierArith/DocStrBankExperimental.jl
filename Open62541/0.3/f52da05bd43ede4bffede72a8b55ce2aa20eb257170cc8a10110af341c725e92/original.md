```julia
struct UA_RepublishRequest
```

Fields:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `subscriptionId::UInt32`
  * `retransmitSequenceNumber::UInt32`
