```
modify_topology(modify_runnable::Functino, topology::Topology)
```

Modify a topology using the `modify_runnable` function which is a one-argument function with the provided topology as argument.

# Example

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
