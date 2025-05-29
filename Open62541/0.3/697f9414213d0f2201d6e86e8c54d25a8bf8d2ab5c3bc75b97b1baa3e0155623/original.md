```julia
struct UA_ServerStatusDataType
```

Fields:

  * `startTime::Int64`
  * `currentTime::Int64`
  * `state::Open62541.UA_ServerState`
  * `buildInfo::Open62541.UA_BuildInfo`
  * `secondsTillShutdown::UInt32`
  * `shutdownReason::Open62541.UA_LocalizedText`
