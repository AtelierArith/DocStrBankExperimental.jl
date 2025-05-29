```
UA_Client_writeUserAccessLevelAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_Byte})
```

UAクライアントAPIを使用して、クライアント`client`を通じてアクセスされるNodeId `nodeId`の属性UserAccessLevelに値`new_val`を書き込みます。
