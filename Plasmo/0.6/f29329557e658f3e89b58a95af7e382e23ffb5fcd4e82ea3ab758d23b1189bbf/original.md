```
JuMP.value(graph::OptiGraph, nvref::NodeVariableRef; result::Int=1)
```

Return the primal value of `nvref` in `graph`. Note that this value is specific to  the optimizer solution to the `graph`. The `nvref` can have different values for  different optigraphs it is contained in.
