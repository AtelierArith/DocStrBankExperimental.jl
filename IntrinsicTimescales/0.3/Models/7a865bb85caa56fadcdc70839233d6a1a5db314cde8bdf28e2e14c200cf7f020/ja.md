```
BaseModel <: AbstractTimescaleModel
```

さまざまな方法を使用したタイムスケール推論のためのベースモデル構造。

# フィールド

  * `data`: 入力時系列データ
  * `time`: データに対応する時間点
  * `data_sum_stats`: データの事前計算された要約統計
  * `fitmethod::Symbol`: 使用するフィッティング方法。オプション: `:abc`, `:advi`, `:acw`
  * `summary_method::Symbol`: 要約統計のタイプ。オプション: `:psd` (パワースペクトル密度) または `:acf` (自己相関)
  * `lags_freqs::AbstractVector{<:Real}`: 要約統計を計算するためのラグ (ACF 用) または周波数 (PSD 用)
  * `prior`: パラメータの事前分布。Vector{Distribution}、単一のDistribution、または "informed_prior" である可能性があります
  * `acwtypes::Union{Vector{Symbol}, Symbol}`: ACW 分析タイプ (例: :ACW50, :ACW0, :ACWe, :tau, :knee)
  * `distance_method::Symbol`: 距離メトリックのタイプ。オプション: `:linear` または `:logarithmic`
  * `dt::Real`: 観測間の時間ステップ
  * `T::Real`: データの総時間範囲
  * `numTrials::Real`: 試行/反復の数
  * `data_mean::Real`: 入力データの平均
  * `data_sd::Real`: 入力データの標準偏差
