```julia
likelihood(M, theta, betas, responses)

```

アイテム応答モデル `M` の尤度を `theta` で評価し、アイテムパラメータ `betas` と応答パターン `responses` を考慮します。

アイテムは独立であると仮定されます。したがって、尤度関数は次のように定義されます。

$$
L(\boldsymbol{u} | \theta, \boldsymbol{\beta}) = \prod_{j=1}^J P(Y_j = y | \theta, \boldsymbol{\beta}_j)
$$

[`loglikelihood`](@ref) も参照してください。
