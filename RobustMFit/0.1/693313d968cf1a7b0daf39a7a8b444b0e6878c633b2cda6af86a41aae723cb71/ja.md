```
GeneralizedTDist(μ::Real, σ::Real,  ν::Real)
```

パラメータ `μ`、`σ` および `ν` を持つ T 分布

# 例

```julia
d = GeneralizedTDist(1, 2, 10)
mean(d)
pdf(d, 1)
```
