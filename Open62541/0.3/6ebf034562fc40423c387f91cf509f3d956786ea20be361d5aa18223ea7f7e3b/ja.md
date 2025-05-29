```julia
struct UA_ReaderGroupConfig
```

フィールド:

  * `name::Open62541.UA_String`
  * `rtLevel::Open62541.UA_PubSubRTLevel`
  * `groupProperties::Open62541.UA_KeyValueMap`
  * `encodingMimeType::Open62541.UA_PubSubEncodingType`
  * `transportSettings::Open62541.UA_ExtensionObject`
  * `securityMode::Open62541.UA_MessageSecurityMode`
