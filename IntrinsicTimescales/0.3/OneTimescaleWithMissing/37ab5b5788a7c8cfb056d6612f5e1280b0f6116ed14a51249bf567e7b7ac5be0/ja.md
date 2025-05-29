```
one_timescale_with_missing_model(data, time, fit_method; kwargs...)
```

欠損データを持つ時系列分析のための OneTimescaleWithMissingModel を構築します。

# 引数

  * `data`: 入力時系列データ（NaN を含む可能性があります）
  * `time`: データに対応する時間点
  * `fit_method`: 使用するフィッティング方法（:abc または :advi）

# キーワード引数

  * `summary_method=:acf`: 要約統計量のタイプ（:psd または :acf）
  * `data_sum_stats=nothing`: 事前に計算された要約統計量
  * `lags_freqs=nothing`: カスタムラグまたは周波数
  * `prior=nothing`: パラメータの事前分布
  * `n_lags=nothing`: ACF のラグの数
  * `distance_method=nothing`: 距離メトリックのタイプ
  * `dt=time[2]-time[1]`: タイムステップ
  * `T=time[end]`: 総時間範囲
  * `numTrials=size(data,1)`: 試行の数
  * `data_mean=nanmean(data)`: データの平均（NaN を除外）
  * `data_sd=nanstd(data)`: データの標準偏差（NaN を除外）
  * `freqlims=nothing`: PSD の周波数制限
  * `freq_idx=nothing`: 周波数選択マスク
  * `dims=ndims(data)`: 分析次元
  * `distance_combined=false`: 結合距離を使用
  * `weights=[0.5, 0.5]`: 距離の重み
  * `data_tau=nothing`: 事前に計算されたタイムスケール

# 返り値

  * `OneTimescaleWithMissingModel`: 指定された分析方法に構成されたモデルインスタンス

# 注意事項

主な使用パターンは4つあります：

1. ACFベースの ABC/ADVI: `summary_method=:acf`, `fit_method=:abc/:advi`
2. PSDベースの ABC/ADVI: `summary_method=:psd`, `fit_method=:abc/:advi`
