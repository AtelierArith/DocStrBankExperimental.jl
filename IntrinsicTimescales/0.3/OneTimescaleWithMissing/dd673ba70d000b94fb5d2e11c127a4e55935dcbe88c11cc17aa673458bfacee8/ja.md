```
OneTimescaleWithMissingModel <: AbstractTimescaleModel
```

欠損値を含む時系列データから単一のタイムスケールを推定するモデルです。

# フィールド

  * `data::AbstractArray{<:Real}`: 入力時系列データ（NaNを含む可能性があります）
  * `time::AbstractVector{<:Real}`: データに対応する時間点
  * `fit_method::Symbol`: フィッティング方法 (:abc または :advi)
  * `summary_method::Symbol`: 要約統計量のタイプ (:psd または :acf)
  * `lags_freqs`: ラグ（ACF用）または周波数（PSD用）
  * `prior`: パラメータの事前分布
  * `distance_method::Symbol`: 距離メトリックのタイプ (:linear または :logarithmic)
  * `data_sum_stats`: 事前計算された要約統計量
  * `dt::Real`: 観測間の時間ステップ
  * `T::Real`: 総時間範囲
  * `numTrials::Real`: 試行/反復の数
  * `data_mean::Real`: 入力データの平均（NaNを除く）
  * `data_sd::Real`: 入力データの標準偏差（NaNを除く）
  * `freqlims`: PSD分析の周波数制限
  * `n_lags`: ACFのラグの数
  * `freq_idx`: 周波数選択のためのブールマスク
  * `dims::Int`: 統計を計算する次元
  * `distance_combined::Bool`: 結合距離メトリックを使用するかどうか
  * `weights::Vector{Real}`: 結合距離のための重み
  * `data_tau::Union{Real, Nothing}`: 事前計算されたタイムスケール
  * `missing_mask::AbstractArray{Bool}`: NaNの位置を示すブールマスク
