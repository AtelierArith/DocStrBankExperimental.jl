```julia
xlog1py(x, y)

```

`y ≥ -1` の場合、$x = 0$ での正しい極限を持つ `x * log(1 + y)` を返します。

```jldoctest
julia> xlog1py(0, -1)
0.0
```
