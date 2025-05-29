```
Product <: MultivariateDistribution
```

N次元の`MultivariateDistribution`は、N個の独立した`UnivariateDistribution`のベクトルから構築されます。

```julia
Product(Uniform.(rand(10), 1)) # 10個の独立した`Uniform`分布からの10次元のProduct。
```

!!! note
    `Product`は非推奨であり、次の破壊的リリースで削除されます。代わりに[`product_distribution`](@ref)を使用してください。

