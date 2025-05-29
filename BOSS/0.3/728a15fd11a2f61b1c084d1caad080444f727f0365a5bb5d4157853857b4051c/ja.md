```
LinModel(; kwargs...)
```

パラメトリックサロゲモデルで、そのパラメータに対して線形です。

このモデル定義は、将来的により一般的な 'NonlinModel' よりも優れたパフォーマンスを提供します。この機能はまだ実装されていないため、現時点では `NonlinModel` を使用するのと同等です。

線形モデルは次のように定義されます。

```
    ϕs = lift(x)
    y = [θs[i]' * ϕs[i] for i in 1:m]
```

ここで、

```
    x = [x₁, ..., xₙ]
    y = [y₁, ..., yₘ]
    θs = [θ₁, ..., θₘ], θᵢ = [θᵢ₁, ..., θᵢₚ]
    ϕs = [ϕ₁, ..., ϕₘ], ϕᵢ = [ϕᵢ₁, ..., ϕᵢₚ]
```

および $n, m, p ∈ R$。

# キーワード

  * `lift::Function`: 上記の定義に従って `lift` 関数 `(::Vector{<:Real}) -> (::Vector{Vector{<:Real}})` を定義します。
  * `theta_priors::AbstractVector{<:UnivariateDistribution}`: 上記の定義に従って、パラメータ `[θ₁₁, ..., θ₁ₚ, ..., θₘ₁, ..., θₘₚ]` の事前分布です。
  * `noise_std_priors::NoiseStdPriors`: 各 `y` 次元のノイズ標準偏差の事前分布です。
