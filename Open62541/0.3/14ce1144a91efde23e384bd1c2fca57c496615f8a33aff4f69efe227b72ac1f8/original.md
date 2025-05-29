```julia
struct UA_EventSource
```

Fields:

  * `next::Ptr{Open62541.UA_EventSource}`
  * `eventSourceType::Open62541.UA_EventSourceType`
  * `name::Open62541.UA_String`
  * `eventLoop::Ptr{Nothing}`
  * `params::Open62541.UA_KeyValueMap`
  * `state::Open62541.UA_EventSourceState`
  * `start::Ptr{Nothing}`
  * `stop::Ptr{Nothing}`
  * `free::Ptr{Nothing}`
