```
GPoisson(λ::Real, ϕ::Real)
```

パラメータ `λ` と `ϕ` を持つ一般化ポアソン分布、詳細は [Article](https://doi.org/10.1016/j.jmaa.2011.11.042) を参照してください。

# 例

```julia
d = GPoisson(5, 0.7)
mean(d)
pdf(d, 1)
```
