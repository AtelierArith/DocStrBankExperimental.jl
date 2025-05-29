```
UA_Client_readWriteMaskAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, out::Ptr{UA_UInt32})
```

UAクライアントAPIを使用して、クライアント`client`を通じてアクセスされるNodeId `nodeId`から属性WriteMaskの値を読み取ります。
