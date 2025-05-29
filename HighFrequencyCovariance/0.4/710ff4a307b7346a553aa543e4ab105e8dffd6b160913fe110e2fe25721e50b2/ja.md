```
estimate_covariance(
    ts::SortedDataFrame,
    assets::Vector{Symbol} = get_assets(ts),
    method::Symbol = :preaveraged_covariance;
    regularisation::Union{Missing,Symbol} = :default,
    regularisation_params::Dict = Dict(),
    only_regulise_if_not_PSD::Bool = false,
    time_grid::Union{Missing,Vector} = missing,
    fixed_spacing::Union{Missing,<:Real} = missing,
    refresh_times::Bool = false,
    rough_guess_number_of_intervals::Integer = 5, # 一般的な入力
    kernel::HFC_Kernel{<:Real} = parzen,
    H::Real = kernel.c_star * mean(a -> length(ts.groupingrows[a]), assets)^0.6,
    m::Integer = 2, # BNHLSパラメータ
    numJ::Integer = 100,
    num_blocks::Integer = 10,
    block_width::Real = (maximum(ts.df[:, ts.time]) - minimum(ts.df[:, ts.time])) /
                        num_blocks,
    microstructure_noise_var::Dict{Symbol,<:Real} = two_scales_volatility(ts, assets)[2], # スペクトル共分散パラメータ
    drop_assets_if_not_enough_data::Bool = false,
    theta::Real = 0.15,
    g::NamedTuple = g, # プレ平均化
    equalweight::Bool = false,
    num_grids::Real = default_num_grids(ts),
    min_obs_for_estimation::Integer = 10,
    if_dont_have_min_obs::Real = NaN,
)
```

これは正則化技術の便利なラッパーです。

### 一般的な入力

  * `ts` - ティックデータ。
  * `assets` - tsから共分散を推定したい資産。
  * `method`  - 使用したい方法。これは `:simple_covariance`、`：bnhls_covariance`、`：spectral_covariance`、`：preaveraged_covariance` または `:two_scales_covariance` であることができます。
  * `regularisation` - 使用する正則化方法。これは `:identity_regularisation`、`：eigenvalue_clean`、`：nearest_correlation_matrix` または `:nearest_psd_matrix` であることができます。また、`：covariance_default`（これは `:nearest_psd_matrix`）または `：correlation_default`（これは `:nearest_correlation_matrix`）を選択することもできます。欠落している場合は、選択した共分散推定方法のデフォルトの正則化方法が使用されます。
  * `regularisation_params` - 選択した正則化方法によって使用されるキーワード引数。
  * `only_regulise_if_not_PSD` - 結果の行列がpsdでない場合のみ正則化されるべきか。

#### `:simple_covariance` メソッドでのみ使用される入力。

  * `time_grid` - リターンを計算するためのグリッド（`:simple_covariance` メソッドのみ）。
  * `fixed_spacing` - 時間グリッドを計算するために使用される間隔。`refresh_times=true` の場合は使用されません（`:simple_covariance` メソッドのみ）。
  * `refresh_times` - 共分散を推定するためにリフレッシュ時間を使用すべきか（`:simple_covariance` メソッドのみ）。
  * `rough_guess_number_of_intervals` - デフォルトの間隔を計算するための大まかな間隔数。`time_grid` または `fixed_spacing` が提供されている場合、または `refresh_times=true` の場合は使用されません（`:simple_covariance` メソッドのみ）。

#### `:bnhls_covariance` メソッドでのみ使用される入力。

  * `kernel` - 使用されるカーネル。詳細についてはbnhls論文を参照してください（`:bnhls_covariance` メソッドのみ）。
  * `H` - 推定に使用されるラグ/リードの数。詳細についてはbnhls論文を参照してください（`:bnhls_covariance` メソッドのみ）。
  * `m` - 平均化するエンドリターンの数（`:bnhls_covariance` メソッドのみ）。

#### `:spectral_covariance` メソッドでのみ使用される入力。

  * `numJ` - J値の数。詳細については論文を参照してください（`:spectral_covariance` メソッドのみ）。
  * `num_blocks` - 時間枠を分割するブロックの数。詳細についてはプレ平均化論文を参照してください（`:spectral_covariance` メソッドのみ）。
  * `block_width` - 時間枠を分割する各ブロックの幅（`:spectral_covariance` メソッドのみ）。
  * `microstructure_noise_var` - 各資産のマイクロストラクチャノイズ分散の推定値（`:spectral_covariance` メソッドのみ）。

#### `:preaveraged_covariance` メソッドでのみ使用される入力。

  * `drop_assets_if_not_enough_data` - 入力された `assets` のすべてを推定するための十分なデータがない場合、持っている資産の相関/ボラティリティのみを計算すべきか。
  * `theta` - シータ値。詳細については論文を参照してください（`:preaveraged_covariance` メソッドのみ）。
  * `g` - プレ平均化方法（名前 "f"）とψ値を含むタプル。詳細については論文を参照してください（`:preaveraged_covariance` メソッドのみ）。

#### `:two_scales_covariance` メソッドでのみ使用される入力。

  * `equalweight` - 2つの異なる資産の線形結合に対して等しい重みを使用すべきか。falseの場合、最適な重みが（ボラティリティから）計算されます（`:two_scales_covariance` メソッドのみ）。
  * `num_grids` - 2スケール推定のために使用されるグリッドの数（`:two_scales_covariance` メソッドのみ）。
  * `min_obs_for_estimation` - 推定のために必要な観測数。これ未満の場合は、以下のフォールバックを使用します。
  * `if_dont_have_min_obs` - 相関を推定するための十分な観測がない場合、何を使用すべきか？

### 戻り値

  * `CovarianceMatrix`
