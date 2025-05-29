```
simple_covariance(
    ts::SortedDataFrame,
    assets::Vector{Symbol} = get_assets(ts);
    regularisation::Union{Missing,Symbol} = :covariance_default,
    regularisation_params::Dict = Dict(),
    only_regulise_if_not_PSD::Bool = false,
    time_grid::Union{Missing,Vector} = missing,
    fixed_spacing::Union{Missing,<:Real} = missing,
    refresh_times::Bool = false,
    rough_guess_number_of_intervals::Integer = 5,
)
```

標準的な教科書の方法で共分散行列を推定します。

### 入力

  * `ts` - ティックデータ。
  * `assets` - ボラティリティを推定したい資産。
  * `regularisation` - 使用する正則化手法を表すシンボル。欠損の場合、正則化は行われません。
  * `regularisation_params` - 正則化アルゴリズムで使用されるキーワード引数。
  * `only_regulise_if_not_PSD` - 行列がすでにPSDでない場合にのみ正則化を試みるべきか。
  * `time_grid` - リターンを計算するためのグリッド。
  * `fixed_spacing` - 時間グリッドを計算するために使用される間隔。`refresh_times=true`の場合は使用されません。
  * `refresh_times` - 共分散を推定するためにリフレッシュ時間を使用すべきか。
  * `rough_guess_number_of_intervals` - デフォルトの間隔を計算するための大まかな間隔数。`time_grid`または`fixed_spacing`が提供されている場合、または`refresh_times=true`の場合は使用されません。

### 戻り値

  * `CovarianceMatrix`。
