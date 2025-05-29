```julia
struct UA_ActivateSessionResponse
```

Fields:

  * `responseHeader::Open62541.UA_ResponseHeader`
  * `serverNonce::Open62541.UA_String`
  * `resultsSize::UInt64`
  * `results::Ptr{UInt32}`
  * `diagnosticInfosSize::UInt64`
  * `diagnosticInfos::Ptr{Open62541.UA_DiagnosticInfo}`
