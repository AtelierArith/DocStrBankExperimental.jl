```julia
struct UA_DatagramDataSetReaderTransportDataType
```

Fields:

  * `address::Open62541.UA_ExtensionObject`
  * `qosCategory::Open62541.UA_String`
  * `datagramQosSize::UInt64`
  * `datagramQos::Ptr{Open62541.UA_ExtensionObject}`
  * `topic::Open62541.UA_String`
