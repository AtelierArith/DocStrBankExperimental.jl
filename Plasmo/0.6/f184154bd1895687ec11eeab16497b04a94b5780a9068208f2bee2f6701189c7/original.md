```
JuMP.set_optimizer(
    node::OptiNode, 
    JuMP.@nospecialize(optimizer_constructor); 
    add_bridges::Bool=true
)
```

Set the optimizer for an optinode.This internally creates a new optigraph that is  used to optimize the node. Calling this method on a node returns the newly created graph.
