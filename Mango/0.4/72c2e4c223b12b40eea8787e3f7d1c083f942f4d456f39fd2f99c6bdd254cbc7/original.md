```
per_node(assign_runnable, topology)
```

Loops over the nodes of the `topology`, calls `assign_runnable` on every node to enable the caller to populate the node. After the loop finished the neighborhoods are created and injected into the agent. 

# Example

```julia
per_node(topology) do node
    add!(node, register(container, TopologyAgent()))
end
```
