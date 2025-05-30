```julia
xlog1py(x, y)

```

`y ≥ -1` の場合に `x * log(1 + y)` を返し、$x = 0$ のときの正しい極限を持ちます。

```jldoctest
julia> xlog1py(0, -1)
0.0
```
