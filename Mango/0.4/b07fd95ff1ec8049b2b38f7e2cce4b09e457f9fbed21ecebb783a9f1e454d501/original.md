```
create_topology(create_runnable)::Topology
```

Create a topology using the `create_runnable` function which is a one-argument function with an initially empty topology as argument.

# Example

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
