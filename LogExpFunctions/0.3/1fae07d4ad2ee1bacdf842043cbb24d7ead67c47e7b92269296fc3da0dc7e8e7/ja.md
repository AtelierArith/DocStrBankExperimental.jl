```julia
xlogx(x)

```

`x * log(x)` を `x ≥ 0` の場合に返し、$x = 0$ の場合は下限を取ることで処理します。

```jldoctest
julia> xlogx(0)
0.0
```
