```
ess(
    samples::AbstractArray{<:Union{Missing,Real}};
    kind=:bulk,
    relative::Bool=false,
    autocov_method=AutocovMethod(),
    split_chains::Int=2,
    maxlag::Int=250,
    kwargs...
)
```

`autocov_method`を用いて、`(draws, [chains[, parameters...]])`の形状を持つ`samples`の有効サンプルサイズ（ESS）を推定します。

オプションで、計算されるESS推定の`kind`を指定できます（下記参照）。一部の`kind`は追加の`kwargs`を受け入れます。

`relative`が`true`の場合、相対ESSが返されます。すなわち、`ess / (draws * chains)`です。

`split_chains`は、各チェーンが分割される数を示します。`split_chains > 1`の場合、診断はチェーン内収束の確認を行います。`d = mod(draws, split_chains) > 0`、すなわちチェーンが均等に分割できない場合、各チェーン内の最初の`d`分割後に1つの描画が破棄されます。分割後、各チェーンには少なくとも3つの描画が必要です。

`maxlag`は、自動共分散が計算される最大ラグを示し、0より大きくなければなりません。

特定の推定量に対して、ESSは少なくとも`100 * chains`であり、$\widehat{R} < 1.01$であることが推奨されます。[^^VehtariGelman2021]

参照: [`AutocovMethod`](@ref), [`FFTAutocovMethod`](@ref), [`BDAAutocovMethod`](@ref), [`rhat`](@ref), [`ess_rhat`](@ref), [`mcse`](@ref)

## ESS推定の種類

`kind`が`Symbol`の場合、次のいずれかの値を取ることができます：

  * `:bulk`: ランク正規化された描画に基づいて計算された基本ESS。この種類は、トレンドやチェーンの異なる位置による分布のバルクでの収束の悪さを診断します。
  * `:tail`: 対称分位数の量子ESSの最小値で、`tail_prob=0.1`は尾部の確率です。この種類は、分布の尾部での収束の悪さを診断します。この種類が選択された場合、`kwargs`には`tail_prob`キーワードが含まれる場合があります。
  * `:basic`: 基本ESS、`kind=Statistics.mean`を指定するのと同等です。

!!! note
    Bulk-ESSは概念的には基本ESSに関連していますが、チェーンが有限分散を持たない場合でも明確に定義されています。[^^VehtariGelman2021] 各パラメータについて、ランク正規化はまず「 tied ranking」を使用して入力をランク付けし、その後ランクを正規分位数に変換することによって進行し、結果が標準的に正規分布されるようにします。この変換は単調です。


そうでない場合、`kind`はESSを推定するための次のいずれかの推定量を指定します：

  * [`Statistics.mean`](@extref)
  * [`Statistics.median`](@extref)
  * [`Statistics.std`](@extref)
  * [`StatsBase.mad`](@extref)
  * `Base.Fix2(Statistics.quantile, p::Real)`

[^VehtariGelman2021]: Vehtari, A., Gelman, A., Simpson, D., Carpenter, B., & Bürkner, P. C. (2021). Rank-normalization, folding, and localization: An improved $\widehat {R}$ for assessing convergence of MCMC. Bayesian Analysis. doi: [10.1214/20-BA1221](https://doi.org/10.1214/20-BA1221) arXiv: [1903.08008](https://arxiv.org/abs/1903.08008)
