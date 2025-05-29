```
per_node(assign_runnable, topology)
```

`topology`のノードをループし、各ノードで`assign_runnable`を呼び出して、呼び出し元がノードを設定できるようにします。ループが終了した後、近隣が作成され、エージェントに注入されます。

# 例

```julia
per_node(topology) do node
    add!(node, register(container, TopologyAgent()))
end
```
