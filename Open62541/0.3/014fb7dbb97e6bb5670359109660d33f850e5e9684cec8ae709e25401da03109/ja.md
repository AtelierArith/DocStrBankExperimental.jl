```julia
struct UA_SessionDiagnosticsDataType
```

フィールド:

  * `sessionId::Open62541.UA_NodeId`
  * `sessionName::Open62541.UA_String`
  * `clientDescription::Open62541.UA_ApplicationDescription`
  * `serverUri::Open62541.UA_String`
  * `endpointUrl::Open62541.UA_String`
  * `localeIdsSize::UInt64`
  * `localeIds::Ptr{Open62541.UA_String}`
  * `actualSessionTimeout::Float64`
  * `maxResponseMessageSize::UInt32`
  * `clientConnectionTime::Int64`
  * `clientLastContactTime::Int64`
  * `currentSubscriptionsCount::UInt32`
  * `currentMonitoredItemsCount::UInt32`
  * `currentPublishRequestsInQueue::UInt32`
  * `totalRequestCount::Open62541.UA_ServiceCounterDataType`
  * `unauthorizedRequestCount::UInt32`
  * `readCount::Open62541.UA_ServiceCounterDataType`
  * `historyReadCount::Open62541.UA_ServiceCounterDataType`
  * `writeCount::Open62541.UA_ServiceCounterDataType`
  * `historyUpdateCount::Open62541.UA_ServiceCounterDataType`
  * `callCount::Open62541.UA_ServiceCounterDataType`
  * `createMonitoredItemsCount::Open62541.UA_ServiceCounterDataType`
  * `modifyMonitoredItemsCount::Open62541.UA_ServiceCounterDataType`
  * `setMonitoringModeCount::Open62541.UA_ServiceCounterDataType`
  * `setTriggeringCount::Open62541.UA_ServiceCounterDataType`
  * `deleteMonitoredItemsCount::Open62541.UA_ServiceCounterDataType`
  * `createSubscriptionCount::Open62541.UA_ServiceCounterDataType`
  * `modifySubscriptionCount::Open62541.UA_ServiceCounterDataType`
  * `setPublishingModeCount::Open62541.UA_ServiceCounterDataType`
  * `publishCount::Open62541.UA_ServiceCounterDataType`
  * `republishCount::Open62541.UA_ServiceCounterDataType`
  * `transferSubscriptionsCount::Open62541.UA_ServiceCounterDataType`
  * `deleteSubscriptionsCount::Open62541.UA_ServiceCounterDataType`
  * `addNodesCount::Open62541.UA_ServiceCounterDataType`
  * `addReferencesCount::Open62541.UA_ServiceCounterDataType`
  * `deleteNodesCount::Open62541.UA_ServiceCounterDataType`
  * `deleteReferencesCount::Open62541.UA_ServiceCounterDataType`
  * `browseCount::Open62541.UA_ServiceCounterDataType`
  * `browseNextCount::Open62541.UA_ServiceCounterDataType`
  * `translateBrowsePathsToNodeIdsCount::Open62541.UA_ServiceCounterDataType`
  * `queryFirstCount::Open62541.UA_ServiceCounterDataType`
  * `queryNextCount::Open62541.UA_ServiceCounterDataType`
  * `registerNodesCount::Open62541.UA_ServiceCounterDataType`
  * `unregisterNodesCount::Open62541.UA_ServiceCounterDataType`
