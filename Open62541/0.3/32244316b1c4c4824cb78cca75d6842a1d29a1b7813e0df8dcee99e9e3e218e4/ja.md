```
UA_Server_readValueRank(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, out::Ptr{UA_Int32})
```

サーバーAPIを使用して、サーバー`server`上のNodeId `nodeId`から属性ValueRankの値を読み取ります。結果は`out`に保存されます。

`out`のメモリは、この関数を使用する前にCによって割り当てられている必要があります。これは`out = UA_Int32_new()`を使用して実行できます。結果のオブジェクトは、使用後に`UA_Int32_delete(out::Ptr{UA_Int32})`を介してクリーンアップする必要があります。
