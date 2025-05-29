```
pair_correlation(particles::Vector{AbstractParticle}, distances::AbstractVector)
```

1つの粒子の配置から等方的なペア相関を計算します。多くの粒子の配置を使用するには、各配置についてこの関数を呼び出し、その後ペア相関の平均を取ります。
