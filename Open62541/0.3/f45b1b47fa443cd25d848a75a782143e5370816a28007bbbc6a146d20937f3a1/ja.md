```julia
struct UA_StructureDefinition
```

フィールド:

  * `defaultEncodingId::Open62541.UA_NodeId`
  * `baseDataType::Open62541.UA_NodeId`
  * `structureType::Open62541.UA_StructureType`
  * `fieldsSize::UInt64`
  * `fields::Ptr{Open62541.UA_StructureField}`
