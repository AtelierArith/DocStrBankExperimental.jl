```julia
struct UA_ContentFilterElementResult
```

Fields:

  * `statusCode::UInt32`
  * `operandStatusCodesSize::UInt64`
  * `operandStatusCodes::Ptr{UInt32}`
  * `operandDiagnosticInfosSize::UInt64`
  * `operandDiagnosticInfos::Ptr{Open62541.UA_DiagnosticInfo}`
