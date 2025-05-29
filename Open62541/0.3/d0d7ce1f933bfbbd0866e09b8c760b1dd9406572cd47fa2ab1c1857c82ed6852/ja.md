```julia
struct UA_CreateSubscriptionRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `requestedPublishingInterval::Float64`
  * `requestedLifetimeCount::UInt32`
  * `requestedMaxKeepAliveCount::UInt32`
  * `maxNotificationsPerPublish::UInt32`
  * `publishingEnabled::Bool`
  * `priority::UInt8`
