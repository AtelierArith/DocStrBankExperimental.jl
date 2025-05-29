```julia
struct UA_DataSetMetaDataType
```

Fields:

  * `namespacesSize::UInt64`
  * `namespaces::Ptr{Open62541.UA_String}`
  * `structureDataTypesSize::UInt64`
  * `structureDataTypes::Ptr{Open62541.UA_StructureDescription}`
  * `enumDataTypesSize::UInt64`
  * `enumDataTypes::Ptr{Open62541.UA_EnumDescription}`
  * `simpleDataTypesSize::UInt64`
  * `simpleDataTypes::Ptr{Open62541.UA_SimpleTypeDescription}`
  * `name::Open62541.UA_String`
  * `description::Open62541.UA_LocalizedText`
  * `fieldsSize::UInt64`
  * `fields::Ptr{Open62541.UA_FieldMetaData}`
  * `dataSetClassId::Open62541.UA_Guid`
  * `configurationVersion::Open62541.UA_ConfigurationVersionDataType`
