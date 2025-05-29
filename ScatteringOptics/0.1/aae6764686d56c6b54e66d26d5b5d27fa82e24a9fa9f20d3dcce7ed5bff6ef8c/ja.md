```
scatter_image(psm::AbstractPhaseScreen, imap::IntensityMap; νref::Number = c_cgs, noise_screen=nothing, rng = Random.default_rng(), use_approx::Bool=true)
```

# 引数

  * `psm::AbstractPhaseScreen`: 位相スクリーンのインスタンス。
  * `imap::IntensityMap`: 強度マップのインスタンス。

# パラメータ

  * `νref::Number=c_cgs`: 散乱効果をシミュレートするために使用される周波数（Hz）。画像の周波数が提供されていない場合、この値が使用されます。
  * `noise_screen=nothing`: 位相スクリーンを生成するために使用されるノイズスクリーン。提供されない場合、ガウシアンノイズスクリーンが生成されます。
  * `rng = Random.default_rng()`: 擬似乱数生成器。
  * `use_approx::Bool=true`: trueの場合、散乱カーネルを計算するために近似解析式が使用されます。そうでない場合は半解析式が使用されます。
