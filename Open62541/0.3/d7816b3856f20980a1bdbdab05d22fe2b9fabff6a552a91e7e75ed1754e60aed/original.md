```julia
struct UA_PubSubConnectionConfig
```

Fields:

  * `name::Open62541.UA_String`
  * `enabled::Bool`
  * `publisherIdType::Open62541.UA_PublisherIdType`
  * `publisherId::Open62541.UA_PublisherId`
  * `transportProfileUri::Open62541.UA_String`
  * `address::Open62541.UA_Variant`
  * `connectionProperties::Open62541.UA_KeyValueMap`
  * `connectionTransportSettings::Open62541.UA_Variant`
  * `eventLoop::Ptr{Open62541.UA_EventLoop}`
