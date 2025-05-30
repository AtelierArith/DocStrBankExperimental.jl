```
choose_agent(choose_agent_function::Function, topology::Topology)
```

ノードに割り当てられるエージェントを選択します。そのためには、`choose_agent_function`を提供する必要があります。この関数は`Node`を引数として受け取り、`Agent`または`Agent...`を返す必要があります。返されたエージェントはノードに割り当てられます。
