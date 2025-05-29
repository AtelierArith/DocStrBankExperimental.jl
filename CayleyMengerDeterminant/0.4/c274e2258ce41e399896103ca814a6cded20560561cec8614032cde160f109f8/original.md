```
binomial2(x::Union{Int,StaticInt,Dynamic}) -> Union{Int,StaticInt,Dynamic}
```

Compute the second binomial coefficient of `x`.

This function is a convenience shorthand for `binomial(x, 2)`.

```julia-repl
julia> binomial2(4)
6
```
