```
HazardBasedDistribution <: ContinuousUnivariateDistribution
```

`HazardBasedDistribution` は、ハザード関数に基づいて分布を構築するタイプです。

このタイプを使用して自分で分布を定式化するには、構造体とハザード関数を実装します。

```julia
struct LogLogistic <: HazardBasedDistribution
    α::Real
    β::Real
end

function JointSurvivalModels.hazard(dist::LogLogistic, t::Real)
    α, β  = dist.α, dist.β
    return ((β / α) * (t / α) ^ (β - 1)) / (1 + (t / α) ^ β)
end
```

`HazardBasedDistribution` は、累積ハザードを計算するための数値積分を実装し、それに基づいて分布を構築します。サンプルを生成するために、ODEを解き、逆変換サンプリングを適用します。
