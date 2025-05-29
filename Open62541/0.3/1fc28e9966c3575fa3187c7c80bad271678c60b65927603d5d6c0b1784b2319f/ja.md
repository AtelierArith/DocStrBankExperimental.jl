```julia
struct UA_InterruptManager
```

フィールド:

  * `eventSource::Open62541.UA_EventSource`
  * `registerInterrupt::Ptr{Nothing}`
  * `deregisterInterrupt::Ptr{Nothing}`
