```
vmapreducethen(f, op, g, As::Vararg{AbstractArray, N}; dims=:, init) where {N}
```

`mapreducethen` のバージョンで、`f` : ℝᴺ → ℝ、`g` : ℝ → ℝ で、次元 `dims` に対して縮約を行います。

# 例

```jldoctest
julia> x, y, z = [1 2; 3 4], [5 6; 7 8], [9 10; 11 12];

julia> vmapreducethen((a, b) -> abs2(a - b), +, √, x, y, dims=2)    # ユークリッド距離
2×1 Matrix{Float64}:
 5.656854249492381
 5.656854249492381

julia> vmapreducethen(*, *, exp, x, y, z, dims=2, init=-1.0)
2×1 Matrix{Float64}:
 0.0
 0.0
```
