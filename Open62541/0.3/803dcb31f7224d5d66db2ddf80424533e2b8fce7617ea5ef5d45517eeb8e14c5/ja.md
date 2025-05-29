```julia
struct UA_CallMethodResult
```

フィールド:

  * `statusCode::UInt32`
  * `inputArgumentResultsSize::UInt64`
  * `inputArgumentResults::Ptr{UInt32}`
  * `inputArgumentDiagnosticInfosSize::UInt64`
  * `inputArgumentDiagnosticInfos::Ptr{Open62541.UA_DiagnosticInfo}`
  * `outputArgumentsSize::UInt64`
  * `outputArguments::Ptr{Open62541.UA_Variant}`
