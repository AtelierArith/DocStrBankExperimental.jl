```julia
xlogy(x, y)

```

`y > 0` の場合、`x * log(y)` を返し、$x = 0$ のときの正しい限界を持ちます。

```jldoctest
julia> xlogy(0, 0)
0.0
```
