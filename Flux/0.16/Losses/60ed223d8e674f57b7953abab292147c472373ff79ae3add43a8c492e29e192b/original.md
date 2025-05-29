```
siamese_contrastive_loss(ŷ, y; margin = 1, agg = mean)
```

Return the [contrastive loss](http://yann.lecun.com/exdb/publis/pdf/hadsell-chopra-lecun-06.pdf) which can be useful for training Siamese Networks. It is given by

```
agg(@. (1 - y) * ŷ^2 + y * max(0, margin - ŷ)^2)
```

Specify `margin` to set the baseline for distance at which pairs are dissimilar.

# Example

```jldoctest
julia> ŷ = [0.5, 1.5, 2.5];

julia> Flux.siamese_contrastive_loss(ŷ, 1:3)
-4.833333333333333

julia> Flux.siamese_contrastive_loss(ŷ, 1:3, margin = 2)
-4.0
```
