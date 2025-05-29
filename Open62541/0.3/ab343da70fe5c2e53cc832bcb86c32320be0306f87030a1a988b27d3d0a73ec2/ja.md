```julia
struct UA_RegisterServer2Response
```

フィールド:

  * `responseHeader::Open62541.UA_ResponseHeader`
  * `configurationResultsSize::UInt64`
  * `configurationResults::Ptr{UInt32}`
  * `diagnosticInfosSize::UInt64`
  * `diagnosticInfos::Ptr{Open62541.UA_DiagnosticInfo}`
