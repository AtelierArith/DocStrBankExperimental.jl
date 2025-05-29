```
JuMP.set_start_value(
    graph::OptiGraph, 
    nvref::NodeVariableRef, 
    value::Union{Nothing,Real}
)
```

Set the start value of variable `nvref` in `graph`. Note that different  graphs can have different start values for node variables.
