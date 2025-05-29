```julia
struct UA_FieldMetaData
```

Fields:

  * `name::Open62541.UA_String`
  * `description::Open62541.UA_LocalizedText`
  * `fieldFlags::UInt16`
  * `builtInType::UInt8`
  * `dataType::Open62541.UA_NodeId`
  * `valueRank::Int32`
  * `arrayDimensionsSize::UInt64`
  * `arrayDimensions::Ptr{UInt32}`
  * `maxStringLength::UInt32`
  * `dataSetFieldId::Open62541.UA_Guid`
  * `propertiesSize::UInt64`
  * `properties::Ptr{Open62541.UA_KeyValuePair}`
