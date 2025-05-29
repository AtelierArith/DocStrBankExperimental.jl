```
UA_Server_readDataType(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, out::Ptr{UA_NodeId})
```

サーバーAPIを使用して、サーバー`server`上のNodeId `nodeId`から属性DataTypeの値を読み取ります。結果は`out`に保存されます。

`out`のメモリは、この関数を使用する前にCによって割り当てられている必要があります。これは`out = UA_NodeId_new()`を使用して実行できます。結果のオブジェクトは、その使用後に`UA_NodeId_delete(out::Ptr{UA_NodeId})`を介してクリーンアップする必要があります。
