```
modify_topology(modify_runnable::Functino, topology::Topology)
```

トポロジーを、提供されたトポロジーを引数とする1引数関数である`modify_runnable`関数を使用して変更します。

# 例

```julia
modify_topology(my_topology) do topology
    agent = register(container, TopologyAgent())
    agent2 = register(container, TopologyAgent())
    agent3 = register(container, TopologyAgent())
    n1 = add_node!(topology, agent)
    n2 = add_node!(topology, agent2)
    n3 = add_node!(topology, agent3)
    add_edge!(topology, n1, n2)
    add_edge!(topology, n1, n3)
end
```
