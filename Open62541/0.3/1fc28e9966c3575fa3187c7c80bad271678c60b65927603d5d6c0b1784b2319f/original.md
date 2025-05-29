```julia
struct UA_InterruptManager
```

Fields:

  * `eventSource::Open62541.UA_EventSource`
  * `registerInterrupt::Ptr{Nothing}`
  * `deregisterInterrupt::Ptr{Nothing}`
