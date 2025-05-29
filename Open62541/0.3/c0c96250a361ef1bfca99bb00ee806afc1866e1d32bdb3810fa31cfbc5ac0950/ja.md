```julia
struct UA_StructureField
```

フィールド:

  * `name::Open62541.UA_String`
  * `description::Open62541.UA_LocalizedText`
  * `dataType::Open62541.UA_NodeId`
  * `valueRank::Int32`
  * `arrayDimensionsSize::UInt64`
  * `arrayDimensions::Ptr{UInt32}`
  * `maxStringLength::UInt32`
  * `isOptional::Bool`
