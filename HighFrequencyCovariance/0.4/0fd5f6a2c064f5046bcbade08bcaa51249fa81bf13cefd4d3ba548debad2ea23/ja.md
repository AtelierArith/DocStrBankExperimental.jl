```
generate_random_path(
   dimensions::Integer,
   ticks::Integer;
   syncronous::Bool = false,
   rng::Union{MersenneTwister,StableRNG} = MersenneTwister(1),
   vol_dist::Distribution = Uniform(
       0.1 / sqrt(252 * 8 * 3600),
       0.5 / sqrt(252 * 8 * 3600),
   ),
   refresh_rate_dist::Distribution = Uniform(0.5, 5.0),
   time_period_per_unit::Dates.Period = Second(1),
   micro_noise_dist::Distribution = Uniform(
       vol_dist.a * sqrt(time_period_ratio(Minute(5), time_period_per_unit)),
       vol_dist.b * sqrt(time_period_ratio(Minute(5), time_period_per_unit)),
   ),
   assets::Union{Vector,Missing} = missing,
   brownian_corr_matrix::Union{Hermitian,Missing} = missing,
   vols::Union{Vector,Missing} = missing,
   rng_timing::Union{MersenneTwister,StableRNG} = MersenneTwister(1),
)
```

指定された次元数とティック数で価格更新のランダムパスを生成します。データが同期的か非同期的か、価格プロセスのボラティリティ、価格更新の（指数的）到着時間のリフレッシュレート、最小および最大のマイクロストラクチャノイズのオプションがあります。

デフォルトは、年率ボラティリティが10％から50％のハイキャップ株を反映するように選択されています。マイクロストラクチャノイズの標準偏差は、5分間のリターンの標準偏差と同じオーダーの大きさです。`vol * sqrt(60*5)`（ボラティリティが秒単位の場合）。期待値として0.5-5秒ごとにティックがリフレッシュされます。

### 入力

  * `dimensions` - 資産の数。
  * `ticks` - 生成するティックの数。
  * `syncronous` - ティックは同期的（各資産ごと）であるべきか、非同期的であるべきか。
  * `rng` - RNGに使用されるRandom.MersenneTwisterまたはStableRNGs.Stable。
  * `vol_dist` - ボラティリティを引き出すための分布（ボラティリティが欠けている場合のみ使用）。
  * `refresh_rate_dist` - リフレッシュレートを引き出すための分布（指数分布のレート）。
  * `time_period_per_unit` - 時間列が対応するべき時間の期間。
  * `micro_noise_dist`  - 資産ごとのマイクロストラクチャノイズの標準偏差を引き出すための分布。
  * `assets` - 使用したい資産の名前。この長さは`dimensions`入力と等しくなければなりません。
  * `brownian_corr_matrix` - 使用する相関行列。入力がない場合は逆ウィシャート分布からサンプリングされます。
  * `vols` - 使用するボラティリティ。これらは`min_noise_var`と`max_noise_var`の間の一様分布からサンプリングされます。

### 戻り値

  * ティックデータの`SortedDataFrame`。
  * ティックデータを生成するために使用された真のデータ生成プロセスを表す`CovarianceMatrix`。
  * 各資産のマイクロストラクチャノイズの分散の`Dict`。
  * 各資産の更新レートの`Dict`。
