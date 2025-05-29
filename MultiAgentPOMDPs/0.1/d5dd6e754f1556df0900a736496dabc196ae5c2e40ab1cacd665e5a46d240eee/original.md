```
function coordination_graph(m::JointMDP)
function coordination_graph(m::JointMDP, s::S) where S
```

Returns the LightGraphs.SimpleGraph (or any appropriate structure) for the coordination graph.
