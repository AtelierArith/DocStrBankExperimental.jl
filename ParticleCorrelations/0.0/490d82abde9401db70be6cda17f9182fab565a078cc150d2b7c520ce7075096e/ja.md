```
pair_correlation(particle_centres::Vector, distances::AbstractVector)
```

1つの粒子の配置から等方的なペア相関を計算します。多くの粒子の配置を使用するには、この関数を各配置に対して呼び出し、その後ペア相関の平均を取ります。
