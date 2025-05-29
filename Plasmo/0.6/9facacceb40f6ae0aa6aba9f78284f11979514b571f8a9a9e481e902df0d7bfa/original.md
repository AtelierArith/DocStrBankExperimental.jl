```
JuMP.dual(graph::OptiGraph, cref::EdgeConstraintRef; result::Int=1)
```

Return the dual value of `cref` in `graph`. Note that this value is specific to  the optimizer solution to the `graph`. The `cref` can have different values for  different optigraphs it is contained in.
