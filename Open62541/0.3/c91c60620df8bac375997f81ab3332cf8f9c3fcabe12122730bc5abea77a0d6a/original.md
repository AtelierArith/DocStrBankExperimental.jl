```julia
struct UA_WriterGroupConfig
```

Fields:

  * `name::Open62541.UA_String`
  * `enabled::Bool`
  * `writerGroupId::UInt16`
  * `publishingInterval::Float64`
  * `keepAliveTime::Float64`
  * `priority::UInt8`
  * `transportSettings::Open62541.UA_ExtensionObject`
  * `messageSettings::Open62541.UA_ExtensionObject`
  * `groupProperties::Open62541.UA_KeyValueMap`
  * `encodingMimeType::Open62541.UA_PubSubEncodingType`
  * `pubsubManagerCallback::Open62541.UA_PubSub_CallbackLifecycle`
  * `maxEncapsulatedDataSetMessageCount::UInt16`
  * `rtLevel::Open62541.UA_PubSubRTLevel`
  * `securityMode::Open62541.UA_MessageSecurityMode`
