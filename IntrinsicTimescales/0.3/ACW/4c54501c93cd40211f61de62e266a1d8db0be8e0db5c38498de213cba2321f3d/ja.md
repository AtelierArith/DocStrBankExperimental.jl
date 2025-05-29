```
acw(data, fs; acwtypes=possible_acwtypes, n_lags=nothing, freqlims=nothing, time=nothing, 
    dims=ndims(data), return_acf=true, return_psd=true, average_over_trials=false,
    trial_dims::Int=setdiff([1, 2], dims)[1], max_peaks::Int=1)
```

時系列データのさまざまな自己相関幅測定を計算します。

# 引数

  * `data::AbstractArray{<:Real}`: 入力時系列データ
  * `fs::Real`: サンプリング周波数
  * `acwtypes::Union{Vector{Symbol}, Symbol}=possible_acwtypes`: 計算するACWのタイプ
  * `n_lags::Union{Int, Nothing}=nothing`: ACF計算のためのラグの数
  * `freqlims::Union{Tuple{Real, Real}, Nothing}=nothing`: スペクトル分析のための周波数制限
  * `time::Union{Vector{Real}, Nothing}=nothing`: 時間ベクトル。これは、欠損データの場合のLomb-Scargle法に必要です。
  * `dims::Int=ndims(data)`: ACWを計算する次元（時間の次元）
  * `return_acf::Bool=true`: ACFを返すかどうか
  * `return_psd::Bool=true`: PSDを返すかどうか
  * `average_over_trials::Bool=false`: 試行ごとにACFまたはPSDを平均するかどうか
  * `trial_dims::Int=setdiff([1, 2], dims)[1]`: 試行ごとにACFまたはPSDを平均する次元（試行の次元）
  * `max_peaks::Int=1`: スペクトル分析でフィットする最大の振動ピークの数
  * `oscillation_peak::Bool=true`: スペクトル分析で振動ピークをフィットするかどうか

# 戻り値

  * 計算されたACW測定のベクトル、入力されたacwtypesに従って順序付けられています

# 注意事項

  * サポートされているACWタイプ：

      * :acw0 - 最初のゼロ交差までの時間
      * :acw50 - 50%減衰までの時間
      * :acweuler - 1/e減衰までの時間
      * :tau - 指数減衰の時間スケール
      * :knee - スペクトル分析からの膝周波数
  * n_lagsが指定されていない場合、1.1 * ACW0を使用します
  * スペクトル測定の場合、freqlimsは全周波数範囲がデフォルトです

```
