```julia
xexpy(x, y)

```

`y > -Inf` の場合は `x * exp(y)` を返し、`y == -Inf` の場合や `x == 0` で `y` が有限の場合はゼロを返します。

```jldoctest
julia> xexpy(1.0, -Inf)
0.0
```
