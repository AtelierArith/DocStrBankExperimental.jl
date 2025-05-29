```julia
MarchenkoPastur <:ContinuousUnivariateDistribution

MarchenkoPastur(λ,σ) 
pdf(d::MarchenkoPastur,x::Real)  
```

  * `λ` : デフォルト `0.5`
  * `σ` : デフォルト `1`

# 例

ρ = 0.5, σ = 1 の MP rv を生成する

```julia
rand(MarchenkoPastur())

1.2656480923753979
```

λ=1.6 の MP 分布の点 0 での密度を計算する

```julia
pdf(MarchenkoPastur(1.6),0)

0.375
```

ρ=0.1 と σ = 2 の 100 個の MP rvs を生成する

```julia
rand(MarchenkoPastur(0.1,2),100)

100-element Vector{Float64}:
 5.31001367107032
 2.3707745658317116
 2.5378523986772343
 2.585256212138476
 ⋮
 3.66799182506567
 6.517865226831382
 3.7628212250212423
 4.582520400697299
```
