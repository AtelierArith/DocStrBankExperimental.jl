```
poisson_loss(ŷ, y; agg = mean)
```

予測された分布 `ŷ` が期待されるポアソン分布 `y` からどれだけ逸脱しているかを返します。計算式は以下の通りです -

```
sum(ŷ .- y .* log.(ŷ)) / size(y, 2)
```

[More information.](https://peltarion.com/knowledge-center/documentation/modeling-view/build-an-ai-model/loss-functions/poisson).

# 例

```jldoctest
julia> y_model = [1, 3, 3];  # データは整数値のみを取るべきです

julia> Flux.poisson_loss(y_model, 1:3)
0.5023128522198171
```
