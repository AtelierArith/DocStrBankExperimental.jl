```julia
struct UA_FieldTargetVariable
```

フィールド:

  * `targetVariable::Open62541.UA_FieldTargetDataType`
  * `externalDataValue::Ptr{Ptr{Open62541.UA_DataValue}}`
  * `targetVariableContext::Ptr{Nothing}`
  * `beforeWrite::Ptr{Nothing}`
  * `afterWrite::Ptr{Nothing}`
