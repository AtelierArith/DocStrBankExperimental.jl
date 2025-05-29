```
choose_agent(choose_agent_function::Function, topology::Topology)
```

Choose the agents, which shall be assigned to the nodes. For this the `choose_agent_function` has to be provided. This  function expects `Node` as argument and shall return an `Agent` or `Agent...`. The returned agent will be assigned to the node.
