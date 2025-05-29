```
siamese_contrastive_loss(ŷ, y; margin = 1, agg = mean)
```

Siamese Networksのトレーニングに役立つ[コントラスト損失](http://yann.lecun.com/exdb/publis/pdf/hadsell-chopra-lecun-06.pdf)を返します。これは次のように与えられます。

```
agg(@. (1 - y) * ŷ^2 + y * max(0, margin - ŷ)^2)
```

`margin`を指定して、ペアが類似していない距離の基準を設定します。

# 例

```jldoctest
julia> ŷ = [0.5, 1.5, 2.5];

julia> Flux.siamese_contrastive_loss(ŷ, 1:3)
-4.833333333333333

julia> Flux.siamese_contrastive_loss(ŷ, 1:3, margin = 2)
-4.0
```
