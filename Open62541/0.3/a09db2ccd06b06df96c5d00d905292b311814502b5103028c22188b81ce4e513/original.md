```julia
struct UA_UABinaryFileDataType
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
  * `schemaLocation::Open62541.UA_String`
  * `fileHeaderSize::UInt64`
  * `fileHeader::Ptr{Open62541.UA_KeyValuePair}`
  * `body::Open62541.UA_Variant`
