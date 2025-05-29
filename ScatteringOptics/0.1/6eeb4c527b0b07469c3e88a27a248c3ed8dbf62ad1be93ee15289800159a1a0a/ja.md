```
scatter_image(sm, imap::IntensityMap; νref::Number = c_cgs, Vx_km_per_s=0.0, Vy_km_per_s=0.0, rng = Random.default_rng(), use_approx::Bool=true)
```

未散乱の同志スカイモデル強度マップ（`imap`）上での完全な星間散乱をシミュレートします。画像の周波数がメタデータに存在する場合、それを使用して散乱効果をシミュレートします。そうでない場合は`νref`が使用されます。

# 引数

  * `sm::AbstractScatteringModel`: 散乱モデルのインスタンス。
  * `imap::IntensityMap`: 強度マップのインスタンス。

# パラメータ

  * `νref::Number=c_cgs`: 散乱効果をシミュレートするために使用されるHz単位の周波数。画像の周波数が提供されていない場合、この値が使用されます。
  * `Vx_km_per_s=0.0`: km/s単位でのx方向の観測者の速度。（将来の実装のためのプレースホルダー）
  * `Vy_km_per_s=0.0`: km/s単位でのy方向の観測者の速度。（将来の実装のためのプレースホルダー）
  * `rng = Random.default_rng()`: 乱数生成器。
  * `use_approx::Bool=true`: trueの場合、散乱カーネルを計算するために近似解析式が使用されます。そうでない場合は半解析式が使用されます。
