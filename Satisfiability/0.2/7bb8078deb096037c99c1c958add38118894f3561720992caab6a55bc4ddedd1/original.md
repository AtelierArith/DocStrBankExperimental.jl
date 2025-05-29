```
a / b
a / 2.0
```

Returns the `Real` division expression `a/b`. Note: `a` and `b` will be converted to `RealExpr`. Use dot broadcasting for vector-valued and matrix-valued expressions.

```julia
@satvariable(a[1:n], Real)
@satvariable(b[1:n, 1:m], Real)
a ./ b
println("typeof a/b: $(typeof(a[1]/b[1]))")
```
