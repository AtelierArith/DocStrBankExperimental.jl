```julia
struct UA_WriteRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `nodesToWriteSize::UInt64`
  * `nodesToWrite::Ptr{Open62541.UA_WriteValue}`
