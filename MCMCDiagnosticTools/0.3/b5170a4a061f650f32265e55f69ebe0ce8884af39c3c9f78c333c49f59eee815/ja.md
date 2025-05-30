```
rhat(samples::AbstractArray{Union{Real,Missing}}; kind::Symbol=:rank, split_chains=2)
```

`samples`の各パラメータに対して$\widehat{R}$診断を計算します。形状は`(draws, [chains[, parameters...]])`です。[^VehtariGelman2021]

`kind`は計算する$\widehat{R}$の種類を示します（下記参照）。

`split_chains`は各チェーンが分割される数を示します。`split_chains > 1`の場合、診断はチェーン内収束をチェックします。`d = mod(draws, split_chains) > 0`、すなわちチェーンが均等に分割できない場合、各チェーン内の最初の`d`分割後に1つの描画が破棄されます。

[`ess`](@ref)、[`ess_rhat`](@ref)、[`rstar`](@ref)も参照してください。

## $\widehat{R}$の種類

サポートされている`kind`は以下の通りです：

  * `:rank`: `kind=:bulk`および`kind=:tail`の最大の$\widehat{R}$。
  * `:bulk`: ランク正規化された描画に基づいて計算された基本的な$\widehat{R}$。この種類は、トレンドやチェーンの異なる位置による分布のバルクでの収束の悪さを診断します。
  * `:tail`: 中央値の周りに折りたたまれた描画に基づいて計算された$\widehat{R}$、その後ランク正規化されます。この種類は、チェーンの異なるスケールによる分布の尾部での収束の悪さを診断します。
  * `:basic`: クラシックな$\widehat{R}$。

[^VehtariGelman2021]: Vehtari, A., Gelman, A., Simpson, D., Carpenter, B., & Bürkner, P. C. (2021). Rank-normalization, folding, and localization: An improved $\widehat {R}$ for assessing convergence of MCMC. Bayesian Analysis. doi: [10.1214/20-BA1221](https://doi.org/10.1214/20-BA1221) arXiv: [1903.08008](https://arxiv.org/abs/1903.08008)
