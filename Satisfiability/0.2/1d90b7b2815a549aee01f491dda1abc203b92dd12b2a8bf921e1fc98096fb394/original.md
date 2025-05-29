```
div(a, b)
div(a, 2)
```

Returns the `Int` division expression `div(a,b)`. Note: `a` and `b` will be converted to `IntExpr`. Use dot broadcasting for vector-valued and matrix-valued expressions.

```julia
@satvariable(a[1:n], Int)
@satvariable(b[1:n, 1:m], Int)
div.(a, b)
println("typeof div(a,b): $(typeof(div(a[1],b[1])))")
```
