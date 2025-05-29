```
simulate!([rng::AbstractRNG,] y::AbstractVector, m::MixedModel{T}[, newdata];
                β = coef(m), σ = m.σ, θ = T[], wts=m.wts)
simulate([rng::AbstractRNG,] m::MixedModel{T}[, newdata];
                β = coef(m), σ = m.σ, θ = T[], wts=m.wts)
```

新しい応答ベクトルをシミュレートし、オプションで事前に割り当てられたベクトルを上書きします。

新しいデータはオプションで表形式で提供できます。

このシミュレーションには、ランダム効果の新しい値をサンプリングすることが含まれています。したがって、`predict`とは対照的に、「新しい」と「古い」/以前に観測されたランダム効果レベルの区別はありません。

`predict`とは異なり、`GeneralizedLinearMixedModel`のための`type`パラメータはありません。モデルとシミュレーションにおけるノイズ項は常に応答スケールにあります。

`wts`引数は、現在、`Binomial`分布を持つ`GeneralizedLinearMixedModel`モデルを除いて無視されます。

!!! note
    `y::AbstractVector`を最初の引数（RNGを除く）として持つ`simulate!`メソッドと、`simulate`メソッドはシミュレートされた応答を返します。これは、最初の引数として`m::MixedModel`を持つ`simulate!`メソッドとは対照的で、モデルの応答を修正し、修正されたモデル全体を返します。

