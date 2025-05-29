```
mae(ŷ, y; agg = mean)
```

平均絶対誤差に対応する損失を返します：

```
agg(abs.(ŷ .- y))
```

# 例

```jldoctest
julia> y_model = [1.1, 1.9, 3.1];

julia> Flux.mae(y_model, 1:3)
0.10000000000000009
```
