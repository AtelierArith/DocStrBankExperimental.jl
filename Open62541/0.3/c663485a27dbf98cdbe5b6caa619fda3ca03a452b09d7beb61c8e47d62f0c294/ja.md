```julia
struct UA_CreateSubscriptionResponse
```

フィールド:

  * `responseHeader::Open62541.UA_ResponseHeader`
  * `subscriptionId::UInt32`
  * `revisedPublishingInterval::Float64`
  * `revisedLifetimeCount::UInt32`
  * `revisedMaxKeepAliveCount::UInt32`
