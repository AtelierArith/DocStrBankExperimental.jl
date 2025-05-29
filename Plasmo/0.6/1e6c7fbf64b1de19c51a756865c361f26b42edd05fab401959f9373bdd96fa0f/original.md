```
@linkconstraint(graph::OptiGraph, expr)
```

Add a linking constraint described by the expression `expr`.

```
@linkconstraint(graph::OptiGraph, ref[i=..., j=..., ...], expr)
```

Add a group of linking  constraints described by the expression `expr` parametrized by `i`, `j`, ...

The @linkconstraint macro works the same way as the `JuMP.@constraint` macro.
