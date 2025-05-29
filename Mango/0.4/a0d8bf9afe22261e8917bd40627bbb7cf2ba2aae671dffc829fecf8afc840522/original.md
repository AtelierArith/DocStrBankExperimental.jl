```
assign_agent(assign_condition::Function, topology::Topology, container::ContainerInterface)
```

Assign all agents of the `container` to the nodes based on the given `assign_condition`, this condition  takes as `Agent` and a `Node` (node.id for the identifier of the node) and shall return a boolean indicating whether the agent shall be assigned to the node.
