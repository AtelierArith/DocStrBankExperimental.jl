```
texpr2expr(x, m::Module=Main)
```

converts a lisp-like tuple expression `x` to the executable expression of Julia.

Example: The expression of `sin(π/6)`

```julia
julia> texpr2expr((:call, :sin, (:call, :/, π, 6)))
:(sin(π / 6))
```
