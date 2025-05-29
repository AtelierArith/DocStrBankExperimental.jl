```julia
struct UA_EventLoop
```

Fields:

  * `logger::Ptr{Open62541.UA_Logger}`
  * `params::Ptr{Open62541.UA_KeyValueMap}`
  * `state::Open62541.UA_EventLoopState`
  * `start::Ptr{Nothing}`
  * `stop::Ptr{Nothing}`
  * `run::Ptr{Nothing}`
  * `free::Ptr{Nothing}`
  * `dateTime_now::Ptr{Nothing}`
  * `dateTime_nowMonotonic::Ptr{Nothing}`
  * `dateTime_localTimeUtcOffset::Ptr{Nothing}`
  * `nextCyclicTime::Ptr{Nothing}`
  * `addCyclicCallback::Ptr{Nothing}`
  * `modifyCyclicCallback::Ptr{Nothing}`
  * `removeCyclicCallback::Ptr{Nothing}`
  * `addTimedCallback::Ptr{Nothing}`
  * `addDelayedCallback::Ptr{Nothing}`
  * `removeDelayedCallback::Ptr{Nothing}`
  * `eventSources::Ptr{Open62541.UA_EventSource}`
  * `registerEventSource::Ptr{Nothing}`
  * `deregisterEventSource::Ptr{Nothing}`
