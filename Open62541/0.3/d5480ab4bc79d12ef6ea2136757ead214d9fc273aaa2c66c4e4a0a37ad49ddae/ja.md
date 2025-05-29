```
UA_Client_writeMinimumSamplingIntervalAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_Double})
```

UAクライアントAPIを使用して、クライアント`client`を通じてアクセスされるNodeId `nodeId`の属性MinimumSamplingIntervalに値`new_val`を書き込みます。
