```
a - b
a - 2
```

Returns the `Int` | `Real` expression `a-b` (inherits the type of `a-b`). Use dot broadcasting for vector-valued and matrix-valued expressions.

```julia
@satvariable(a[1:n], Int)
@satvariable(b[1:n, 1:m], Int)
a .- b
println("typeof a-b: $(typeof(a[1] - b[1]))")

@satvariable(c, Real)
println("typeof a-c: $(typeof(a[1] - c))")

@satvariable(z, Bool)
a .- z
println("typeof a-z: $(typeof(a[1] - z))")
```
