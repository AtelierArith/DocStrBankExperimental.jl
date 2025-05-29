```
substitute(expr, dict; fold=true)
```

substitute any subexpression that matches a key in `dict` with the corresponding value. If `fold=false`, expressions which can be evaluated won't be evaluated.

```julia
julia> substitute(1+sqrt(y), Dict(y => 2), fold=true)
2.414213562373095
julia> substitute(1+sqrt(y), Dict(y => 2), fold=false)
1 + sqrt(2)
```
