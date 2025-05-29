```
kldiv(q::T, p::T) where T<:ExpFamilyDistribution
```

同じタイプの2つの分布間のKLダイバージェンスを計算します（例：`kldiv(Normal, Normal)`、`kldiv(Dirichlet, Dirichlet)`、...）
