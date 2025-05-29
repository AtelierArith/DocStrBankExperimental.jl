```julia
xexpx(x)

```

`x > -Inf` の場合は `x * exp(x)` を返し、`x == -Inf` の場合はゼロを返します。

```jldoctest
julia> xexpx(-Inf)
0.0
```
