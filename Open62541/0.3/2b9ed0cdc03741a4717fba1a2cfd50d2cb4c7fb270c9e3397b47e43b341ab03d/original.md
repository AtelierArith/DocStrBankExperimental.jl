```julia
struct UA_ParsingResult
```

Fields:

  * `statusCode::UInt32`
  * `dataStatusCodesSize::UInt64`
  * `dataStatusCodes::Ptr{UInt32}`
  * `dataDiagnosticInfosSize::UInt64`
  * `dataDiagnosticInfos::Ptr{Open62541.UA_DiagnosticInfo}`
