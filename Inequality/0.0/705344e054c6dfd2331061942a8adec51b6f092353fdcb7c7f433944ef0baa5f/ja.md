```
poverty_gap(v, z)
```

ベクトル `v` の貧困ギャップを指定された貧困閾値 `z` で計算します。

# 例

```julia
julia> using Inequality
julia> poverty_gap([8, 5, 1, 3, 5, 6, 7, 6, 3], 4)
0.1388888888888889
```
