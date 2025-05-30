```julia
struct MAP{T<:Distributions.Distribution{Distributions.Univariate, Distributions.Continuous}, U<:Roots.AbstractSecantMethod} <: PersonParameters.PersonParameterAlgorithm
```

項目応答モデルの人物パラメータの最大事後推定。`prior`を使用して能力値の事前分布を指定します。

## フィールド

  * `prior`: 人物の能力の事前分布
  * `root_finding_alg`
