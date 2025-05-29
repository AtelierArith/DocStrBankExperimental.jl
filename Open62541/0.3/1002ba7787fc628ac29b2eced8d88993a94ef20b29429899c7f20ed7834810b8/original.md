```julia
struct UA_ModifySubscriptionRequest
```

Fields:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `subscriptionId::UInt32`
  * `requestedPublishingInterval::Float64`
  * `requestedLifetimeCount::UInt32`
  * `requestedMaxKeepAliveCount::UInt32`
  * `maxNotificationsPerPublish::UInt32`
  * `priority::UInt8`
