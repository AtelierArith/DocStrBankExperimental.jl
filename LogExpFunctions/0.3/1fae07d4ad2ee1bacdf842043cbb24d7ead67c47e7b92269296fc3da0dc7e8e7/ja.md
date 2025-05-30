```julia
xlogx(x)

```

`x * log(x)` を返します。`x ≥ 0` の場合、$x = 0$ のときは下限を取ります。

```jldoctest
julia> xlogx(0)
0.0
```
