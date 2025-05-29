```
gen_entropy(v, α)

ベクトル `v` の一般化エントロピー指数を指定されたパラメータ `α` で計算します。
```

# 例

```julia
julia> using Inequality
julia> gen_entropy([8, 5, 1, 3, 5, 6, 7, 6, 3], 2)
0.09039256198347094
```
