```
two_scales_covariance(
    ts::SortedDataFrame,
    assets::Vector{Symbol} = get_assets(ts);
    regularisation::Union{Missing,Symbol} = :correlation_default,
    regularisation_params::Dict = Dict(),
    only_regulise_if_not_PSD::Bool = false,
    equalweight::Bool = false,
    num_grids::Real = default_num_grids(ts),
    min_obs_for_estimation::Integer = 10,
    if_dont_have_min_obs::Real = NaN,
)
```

二重スケール共分散法を使用した共分散行列の推定。

### 入力

  * `ts` - ティックデータ。
  * `assets` - ボラティリティを推定したい資産。
  * `regularisation` - 使用する正則化手法を表すシンボル。欠損の場合は正則化は行われません。
  * `regularisation_params` - 正則化アルゴリズムで使用されるキーワード引数。
  * `only_regulise_if_not_PSD` - 行列がすでにPSDでない場合にのみ正則化を試みるべきか。
  * `equalweight` - 資産の2つの異なる線形結合に対して等しい重みを使用するべきか。falseの場合は、最適な重みが計算されます（ボラティリティから）。
  * `num_grids` - 二重スケール推定に使用されるグリッドの数。
  * `min_obs_for_estimation` - 推定に必要な観測数。これ未満の場合は、以下のフォールバックを使用します。
  * `if_dont_have_min_obs` - 相関を推定するための十分な観測がない場合、何を使用すべきか？

### 戻り値

  * `CovarianceMatrix`。
