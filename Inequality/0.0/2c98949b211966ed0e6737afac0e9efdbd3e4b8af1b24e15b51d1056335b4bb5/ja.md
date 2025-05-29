```
headcount(v, z)
```

ベクトル `v` の指定された貧困閾値 `z` におけるヘッドカウント比を計算します。

# 例

```julia
julia> using Inequality
julia> headcount([8, 5, 1, 3, 5, 6, 7, 6, 3], 4)
0.3333333333333333
```
