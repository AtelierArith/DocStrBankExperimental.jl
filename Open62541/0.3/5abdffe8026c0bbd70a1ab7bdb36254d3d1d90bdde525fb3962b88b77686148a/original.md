```julia
struct UA_MonitoringParameters
```

Fields:

  * `clientHandle::UInt32`
  * `samplingInterval::Float64`
  * `filter::Open62541.UA_ExtensionObject`
  * `queueSize::UInt32`
  * `discardOldest::Bool`
