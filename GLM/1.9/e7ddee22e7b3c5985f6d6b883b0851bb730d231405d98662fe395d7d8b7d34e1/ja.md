```
devresid(D, y, μ::Real)
```

`y`からの`μ`の二乗偏差残差を分布`D`に対して返します。

GLMの偏差は、二乗偏差残差の合計として評価できます。これはこれらの値の主な使用目的です。実際の偏差残差は、プロットのために、この値の符号付き平方根です。

```julia
sign(y - μ) * sqrt(devresid(D, y, μ))
```

# 例

```jldoctest; setup = :(using GLM: Bernoulli, Normal, devresid)
julia> devresid(Normal(), 0, 0.25) ≈ abs2(0.25)
true

julia> devresid(Bernoulli(), 1, 0.75) ≈ -2*log(0.75)
true

julia> devresid(Bernoulli(), 0, 0.25) ≈ -2*log1p(-0.25)
true
```
