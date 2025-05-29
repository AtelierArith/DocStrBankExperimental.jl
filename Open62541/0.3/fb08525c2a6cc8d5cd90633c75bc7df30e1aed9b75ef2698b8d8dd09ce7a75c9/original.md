```julia
struct UA_MonitoredItemCreateResult
```

Fields:

  * `statusCode::UInt32`
  * `monitoredItemId::UInt32`
  * `revisedSamplingInterval::Float64`
  * `revisedQueueSize::UInt32`
  * `filterResult::Open62541.UA_ExtensionObject`
