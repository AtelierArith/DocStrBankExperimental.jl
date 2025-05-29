```
atkinson(v, ϵ)
```

ベクトル `v` のアトキンソン指数を指定された不平等嫌悪パラメータ `ϵ` で計算します。

# 例

```julia
julia> using Inequality
julia> atkinson([8, 5, 1, 3, 5, 6, 7, 6, 3], 1.2)
0.1631765870035865
```
