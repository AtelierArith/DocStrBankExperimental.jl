```julia
struct UA_ProgramDiagnostic2DataType
```

フィールド:

  * `createSessionId::Open62541.UA_NodeId`
  * `createClientName::Open62541.UA_String`
  * `invocationCreationTime::Int64`
  * `lastTransitionTime::Int64`
  * `lastMethodCall::Open62541.UA_String`
  * `lastMethodSessionId::Open62541.UA_NodeId`
  * `lastMethodInputArgumentsSize::UInt64`
  * `lastMethodInputArguments::Ptr{Open62541.UA_Argument}`
  * `lastMethodOutputArgumentsSize::UInt64`
  * `lastMethodOutputArguments::Ptr{Open62541.UA_Argument}`
  * `lastMethodInputValuesSize::UInt64`
  * `lastMethodInputValues::Ptr{Open62541.UA_Variant}`
  * `lastMethodOutputValuesSize::UInt64`
  * `lastMethodOutputValues::Ptr{Open62541.UA_Variant}`
  * `lastMethodCallTime::Int64`
  * `lastMethodReturnStatus::UInt32`
