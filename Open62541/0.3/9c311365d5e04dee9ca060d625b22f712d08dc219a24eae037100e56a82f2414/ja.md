```
UA_Client_writeDescriptionAttribute_async(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, newValue::Ptr{UA_LocalizedText},
    callback::UA_ClientAsyncServiceCallback, userdata::Ptr{Cvoid},
    requestId::UInt32)::UA_StatusCode
```

非同期クライアントAPIを使用して、クライアント`client`を介してアクセスされるNodeId `nodeId`の属性Descriptionに値`newValue`を書き込みます。
