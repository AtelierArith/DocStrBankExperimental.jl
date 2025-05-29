```julia
struct UA_SubscriptionDiagnosticsDataType
```

Fields:

  * `sessionId::Open62541.UA_NodeId`
  * `subscriptionId::UInt32`
  * `priority::UInt8`
  * `publishingInterval::Float64`
  * `maxKeepAliveCount::UInt32`
  * `maxLifetimeCount::UInt32`
  * `maxNotificationsPerPublish::UInt32`
  * `publishingEnabled::Bool`
  * `modifyCount::UInt32`
  * `enableCount::UInt32`
  * `disableCount::UInt32`
  * `republishRequestCount::UInt32`
  * `republishMessageRequestCount::UInt32`
  * `republishMessageCount::UInt32`
  * `transferRequestCount::UInt32`
  * `transferredToAltClientCount::UInt32`
  * `transferredToSameClientCount::UInt32`
  * `publishRequestCount::UInt32`
  * `dataChangeNotificationsCount::UInt32`
  * `eventNotificationsCount::UInt32`
  * `notificationsCount::UInt32`
  * `latePublishRequestCount::UInt32`
  * `currentKeepAliveCount::UInt32`
  * `currentLifetimeCount::UInt32`
  * `unacknowledgedMessageCount::UInt32`
  * `discardedMessageCount::UInt32`
  * `monitoredItemCount::UInt32`
  * `disabledMonitoredItemCount::UInt32`
  * `monitoringQueueOverflowCount::UInt32`
  * `nextSequenceNumber::UInt32`
  * `eventQueueOverFlowCount::UInt32`
