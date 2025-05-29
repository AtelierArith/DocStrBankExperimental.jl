```
spectral_covariance(
    ts::SortedDataFrame,
    assets::Vector{Symbol} = get_assets(ts);
    regularisation::Union{Missing,Symbol} = :covariance_default,
    regularisation_params::Dict = Dict(),
    only_regulise_if_not_PSD::Bool = false,
    numJ::Integer = 100,
    num_blocks::Integer = 10,
    block_width::Real = (maximum(ts.df[:, ts.time]) - minimum(ts.df[:, ts.time])) /
                        num_blocks,
    microstructure_noise_var::Dict{Symbol,<:Real} = two_scales_volatility(ts, assets)[2],
)
```

スペクトル共分散法を使用した共分散行列の推定。

### 入力

  * `ts` - ティックデータ。
  * `assets` - ボラティリティを推定したい資産。
  * `regularisation` - 使用する正則化手法を表すシンボル。欠損の場合は正則化は行われません。
  * `regularisation_params` - 正則化アルゴリズムで使用されるキーワード引数。
  * `only_regulise_if_not_PSD` - 行列がすでにPSDでない場合にのみ正則化を試みるべきか。
  * `numJ` - J値の数。詳細は論文を参照してください。
  * `num_blocks` - 時間枠を分割するブロックの数。詳細は論文を参照してください。
  * `block_width` - 時間枠を分割する各ブロックの幅。
  * `microstructure_noise_var` - 各資産のマイクロストラクチャノイズ分散の推定値。

### 戻り値

  * `CovarianceMatrix`。

### 参考文献

Bibinger M, Hautsch N, Malec P, Reiss M (2014). “Estimating the quadratic covariation matrix from noisy observations: Local method of moments and efficiency.” The Annals of Statistics, 42(4), 1312–1346. doi:10.1214/14-AOS1224.
