```
RAE(d::UnivariateDistribution, spec::MSetting, biasCorr::Union{Symbol, String})
RAE(d::UnivariateDistribution, spec::Vector{MSetting}, biasCorr::Union{Symbol, String})
RAE(x::Vector{Real}, d::UnivariateDistribution, spec::MSetting, biasCorr::Union{Symbol, String})
RAE(x::Vector{Real}, d::UnivariateDistribution, spec::Vector{MSetting}, biasCorr::Union{Symbol, String})
```

M推定量の相対漸近効率は、最尤推定と比較されます。計算は[`AVar`](@ref AVar)および[`FInfo`](@ref FInfo)に基づいています。

分布`d`が複数のパラメータを持つ場合、キーワード引数`single`を`single = true`（デフォルト）に設定すると、単一の分散が比較されます。`single = false`は、det(Σ₁)/det(Σ₂)のp-th根を計算します。ここで、Σ₁はML推定量の共分散行列、Σ₂はM推定量の共分散行列です。

# 例

```julia
d = Poisson(10)
x = rand(d, 200)
spec = Huber(1.5)
λ = Mfit(x, d, spec)
dFit = Poisson(λ)

RAE(dFit, spec, :L)
RAE(x, dFit, spec, :L)

d = Normal(0, 1)
x = rand(d, 200)
spec = [Huber(1.5), Huber(2.5)]
ests = Mfit(x, d, spec)
dFit = NewDist(d, ests)

RAE(dFit, spec, :L, n = 500)
RAE(dFit, spec, :L, n = 500, single = false)
RAE(x, dFit, spec, :L)
```

引数の追加説明については[`AVar`](@ref AVar)を参照してください。
