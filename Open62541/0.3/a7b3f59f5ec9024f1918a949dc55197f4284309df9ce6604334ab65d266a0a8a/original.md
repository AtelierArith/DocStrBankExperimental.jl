```julia
struct UA_DeleteSubscriptionsResponse
```

Fields:

  * `responseHeader::Open62541.UA_ResponseHeader`
  * `resultsSize::UInt64`
  * `results::Ptr{UInt32}`
  * `diagnosticInfosSize::UInt64`
  * `diagnosticInfos::Ptr{Open62541.UA_DiagnosticInfo}`
