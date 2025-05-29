```
RandomVariable(dist::UnivariateDistribution, name::Symbol)
```

ユニバリアント分布からのランダム変数を定義し、名前を付けます。

# 例

```jldoctest
julia> RandomVariable(Normal(), :x)
RandomVariable(Normal{Float64}(μ=0.0, σ=1.0), :x)

julia> RandomVariable(Exponential(1), :x)
RandomVariable(Exponential{Float64}(θ=1.0), :x)
```
