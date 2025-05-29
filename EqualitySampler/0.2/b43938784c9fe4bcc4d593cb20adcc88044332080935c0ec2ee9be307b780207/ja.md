```
CustomInclusionPartitionDistribution(k::T, logpdf::NTuple{N, Float64})
```

CustomInclusionPartitionDistributionは、モデルの確率がパーティションのサイズによって完全に決定される点で、BetaBinomialPartitionDistributionに似ています。BetaBinomialPartitionDistributionが確率を得るためにBetaBinomial分布を使用するのに対し、CustomInclusionPartitionDistributionは任意の確率ベクトルを指定するために使用できます。この分布は、特定のサイズのパーティションから均等にサンプリングするのに特に便利です。例えば：

```julia
rand(CustomInclusionPartitionDistribution(4, ntuple(i->log(i==1), Val(4)))) # 常にすべて等しい (1パラメータ)
rand(CustomInclusionPartitionDistribution(4, ntuple(i->log(i==3), Val(4)))) # 常に3パラメータ
rand(CustomInclusionPartitionDistribution(4, ntuple(i->log(i==4), Val(4)))) # 常に完全に異なる (4パラメータ)
```

この関数は、sum(exp, logpdf) ≈ 1.0であるかどうかをチェックしません。それは呼び出し元の責任です。 ```
