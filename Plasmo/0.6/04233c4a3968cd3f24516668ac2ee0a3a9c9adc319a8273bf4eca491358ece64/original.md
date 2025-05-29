```
JuMP.add_constraint(graph::OptiGraph, con::JuMP.AbstractConstraint, name::String="")
```

Add a new constraint to `graph`. This method is called internall when a user uses the  JuMP.@constraint macro.
