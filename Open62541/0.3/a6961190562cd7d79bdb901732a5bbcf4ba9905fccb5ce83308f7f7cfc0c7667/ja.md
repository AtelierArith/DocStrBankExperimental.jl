```julia
struct UA_PublishRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `subscriptionAcknowledgementsSize::UInt64`
  * `subscriptionAcknowledgements::Ptr{Open62541.UA_SubscriptionAcknowledgement}`
