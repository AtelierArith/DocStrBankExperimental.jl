```julia
struct UA_DatagramWriterGroupTransport2DataType
```

フィールド:

  * `messageRepeatCount::UInt8`
  * `messageRepeatDelay::Float64`
  * `address::Open62541.UA_ExtensionObject`
  * `qosCategory::Open62541.UA_String`
  * `datagramQosSize::UInt64`
  * `datagramQos::Ptr{Open62541.UA_ExtensionObject}`
  * `discoveryAnnounceRate::UInt32`
  * `topic::Open62541.UA_String`
