```julia
struct UA_CallRequest
```

Fields:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `methodsToCallSize::UInt64`
  * `methodsToCall::Ptr{Open62541.UA_CallMethodRequest}`
