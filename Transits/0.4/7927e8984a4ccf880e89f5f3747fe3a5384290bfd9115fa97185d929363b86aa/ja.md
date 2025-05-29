```
Kipping13()
```

2つのパラメータの肢暗化係数に対する非情報的事前分布を*三角サンプリング*を使用して生成します（[Kipping 2013](https://ui.adsabs.harvard.edu/abs/2013MNRAS.435.2152K/)）。

# 例

```jldoctest
julia> using StableRNGs; rng = StableRNG(10);

julia> rand(rng, Kipping13())
2-element Vector{Float64}:
  0.3361047299132651
 -0.025681638815114587

julia> rand(rng, Kipping13(), 5)
2×5 Matrix{Float64}:
 0.0621057   0.992689   1.77965    0.784055  0.186386
 0.0659477  -0.236613  -0.795884  -0.187791  0.592194
```

# 参考文献

> [Kipping (2013)](https://ui.adsabs.harvard.edu/abs/2013MNRAS.435.2152K/)
>
> "2つのパラメータ法のための肢暗化係数の効率的で非情報的なサンプリング"

