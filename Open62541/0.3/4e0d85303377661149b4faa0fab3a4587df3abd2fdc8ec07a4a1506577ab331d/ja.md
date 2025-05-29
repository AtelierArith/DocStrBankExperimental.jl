```julia
struct UA_ReadRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `maxAge::Float64`
  * `timestampsToReturn::Open62541.UA_TimestampsToReturn`
  * `nodesToReadSize::UInt64`
  * `nodesToRead::Ptr{Open62541.UA_ReadValueId}`
