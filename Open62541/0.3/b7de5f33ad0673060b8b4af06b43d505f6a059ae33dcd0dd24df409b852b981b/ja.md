```julia
struct UA_PubSubConnectionDataType
```

フィールド:

  * `name::Open62541.UA_String`
  * `enabled::Bool`
  * `publisherId::Open62541.UA_Variant`
  * `transportProfileUri::Open62541.UA_String`
  * `address::Open62541.UA_ExtensionObject`
  * `connectionPropertiesSize::UInt64`
  * `connectionProperties::Ptr{Open62541.UA_KeyValuePair}`
  * `transportSettings::Open62541.UA_ExtensionObject`
  * `writerGroupsSize::UInt64`
  * `writerGroups::Ptr{Open62541.UA_WriterGroupDataType}`
  * `readerGroupsSize::UInt64`
  * `readerGroups::Ptr{Open62541.UA_ReaderGroupDataType}`
