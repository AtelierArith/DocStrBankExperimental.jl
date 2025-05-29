```julia
struct UA_ProgramDiagnosticDataType
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
  * `lastMethodCallTime::Int64`
  * `lastMethodReturnStatus::Open62541.UA_StatusResult`
