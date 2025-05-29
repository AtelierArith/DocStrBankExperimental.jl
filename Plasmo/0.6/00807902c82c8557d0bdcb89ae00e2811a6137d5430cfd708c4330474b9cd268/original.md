```
JuMP.set_optimizer(
    graph::OptiGraph, 
    JuMP.@nospecialize(optimizer_constructor); 
    add_bridges::Bool=true
)
```

Set the optimizer on `graph` by passing an `optimizer_constructor`.
