```julia
struct UA_PublishedVariableDataType
```

Fields:

  * `publishedVariable::Open62541.UA_NodeId`
  * `attributeId::UInt32`
  * `samplingIntervalHint::Float64`
  * `deadbandType::UInt32`
  * `deadbandValue::Float64`
  * `indexRange::Open62541.UA_String`
  * `substituteValue::Open62541.UA_Variant`
  * `metaDataPropertiesSize::UInt64`
  * `metaDataProperties::Ptr{Open62541.UA_QualifiedName}`
