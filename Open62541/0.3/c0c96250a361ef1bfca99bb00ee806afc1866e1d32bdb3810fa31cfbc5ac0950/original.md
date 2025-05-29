```julia
struct UA_StructureField
```

Fields:

  * `name::Open62541.UA_String`
  * `description::Open62541.UA_LocalizedText`
  * `dataType::Open62541.UA_NodeId`
  * `valueRank::Int32`
  * `arrayDimensionsSize::UInt64`
  * `arrayDimensions::Ptr{UInt32}`
  * `maxStringLength::UInt32`
  * `isOptional::Bool`
