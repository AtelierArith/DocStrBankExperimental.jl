```
UA_Server_readIsAbstract(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, out::Ptr{UA_Boolean})
```

サーバーAPIを使用して、サーバー`server`上のNodeId `nodeId`から属性IsAbstractの値を読み取ります。結果は`out`に保存されます。

`out`のメモリは、この関数を使用する前にCによって割り当てられる必要があります。これは`out = UA_Boolean_new()`で実行できます。結果のオブジェクトは、使用後に`UA_Boolean_delete(out::Ptr{UA_Boolean})`を介してクリーンアップする必要があります。
