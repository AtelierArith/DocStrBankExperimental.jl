```julia
struct UA_ConnectionManager
```

Fields:

  * `eventSource::Open62541.UA_EventSource`
  * `protocol::Open62541.UA_String`
  * `openConnection::Ptr{Nothing}`
  * `sendWithConnection::Ptr{Nothing}`
  * `closeConnection::Ptr{Nothing}`
  * `allocNetworkBuffer::Ptr{Nothing}`
  * `freeNetworkBuffer::Ptr{Nothing}`
