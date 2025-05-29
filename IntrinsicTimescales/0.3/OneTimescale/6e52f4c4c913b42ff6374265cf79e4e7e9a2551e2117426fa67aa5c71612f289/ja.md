```
OneTimescaleModel <: AbstractTimescaleModel
```

時系列データから単一のタイムスケールを推定するためのモデルで、オルンシュタイン-ウーレンベック過程を使用します。直接作成するのではなく、`one_timescale_model` コンストラクタ関数を使用することをお勧めします。

# フィールド

  * `data::AbstractArray{<:Real}`: 入力時系列データ
  * `time::AbstractVector{<:Real}`: データに対応する時間点
  * `fit_method::Symbol`: フィッティング方法 (:abc または :advi)
  * `summary_method::Symbol`: サマリー統計のタイプ (:psd または :acf)
  * `lags_freqs`: ラグ (ACF 用) または周波数 (PSD 用)
  * `prior`: パラメータの事前分布
  * `distance_method::Symbol`: 距離メトリックのタイプ (:linear または :logarithmic)
  * `data_sum_stats`: 事前計算されたサマリー統計
  * `dt::Real`: 観測間の時間ステップ
  * `T::Real`: 総時間範囲
  * `numTrials::Real`: 試行/反復の数
  * `data_mean::Real`: 入力データの平均
  * `data_sd::Real`: 入力データの標準偏差
  * `freqlims`: PSD 分析の周波数制限
  * `n_lags`: ACF のラグの数
  * `freq_idx`: 周波数選択のためのブールマスク
  * `dims::Int`: 統計を計算する次元
  * `distance_combined::Bool`: 結合距離メトリックを使用するかどうか
  * `weights::Vector{Real}`: 結合距離の重み
  * `data_tau::Union{Real, Nothing}`: 事前計算されたタイムスケール
  * `u0::Union{Vector{Real}, Nothing}`: 初期パラメータの推測
