```
assign_agent(assign_condition::Function, topology::Topology, container::ContainerInterface)
```

`container`のすべてのエージェントを、指定された`assign_condition`に基づいてノードに割り当てます。この条件は`Agent`と`Node`（ノードの識別子としてnode.idを使用）を引数に取り、エージェントがノードに割り当てられるべきかどうかを示すブール値を返す必要があります。
