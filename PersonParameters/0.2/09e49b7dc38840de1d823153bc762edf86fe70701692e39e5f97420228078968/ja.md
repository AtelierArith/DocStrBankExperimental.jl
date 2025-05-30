```julia
struct EAP{T<:Distributions.Distribution{Distributions.Univariate, Distributions.Continuous}, U<:Real} <: PersonParameters.PersonParameterAlgorithm
```

項目応答モデルの人のパラメータの期待後方推定。`prior`を使用して能力値の事前分布を指定します。

`domain`は数値積分のためのドメインを制限するために使用できます。デフォルトは`extrema(prior)`であり、事前分布の全サポートを参照します。

## フィールド

  * `prior`: 人の能力の事前分布
  * `domain`: 積分ドメイン
