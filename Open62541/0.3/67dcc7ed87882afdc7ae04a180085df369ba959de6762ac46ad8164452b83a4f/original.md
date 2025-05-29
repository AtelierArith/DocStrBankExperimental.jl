```julia
struct UA_DatagramConnectionTransport2DataType
```

Fields:

  * `discoveryAddress::Open62541.UA_ExtensionObject`
  * `discoveryAnnounceRate::UInt32`
  * `discoveryMaxMessageSize::UInt32`
  * `qosCategory::Open62541.UA_String`
  * `datagramQosSize::UInt64`
  * `datagramQos::Ptr{Open62541.UA_ExtensionObject}`
