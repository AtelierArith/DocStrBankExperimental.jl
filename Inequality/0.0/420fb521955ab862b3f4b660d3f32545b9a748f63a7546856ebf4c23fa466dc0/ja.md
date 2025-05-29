```
watts(v, k)

ベクトル `v` のワッツ貧困指数を指定された絶対貧困ライン `k` で計算します。
```

# 例

```julia
julia> using Inequality
julia> watts([8, 5, 1, 3, 5, 6, 7, 6, 3], 4)
0.217962056224828
```
