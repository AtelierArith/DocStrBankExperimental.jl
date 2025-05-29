```
create_topology(create_runnable)::Topology
```

`create_runnable`関数を使用してトポロジーを作成します。この関数は、最初は空のトポロジーを引数として受け取る1引数関数です。

# 例

```julia
topology = create_topology() do topology
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
