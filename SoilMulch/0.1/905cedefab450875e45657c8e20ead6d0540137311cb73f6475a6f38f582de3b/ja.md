`soil_water_balance(rain, eto, cf, s, sh, sw, sstar, ks, β, n, zr, rth, ce, ct, dt)`

マルチングなしの条件下での土壌水分バランスを計算します。

# 引数

  * `rain::Float64`: 降雨量。
  * `eto::Float64`: 参照蒸発散。
  * `cf::Float64`: 作物被覆率。
  * `s::Float64`: 土壌水分。
  * `sh::Float64`: ウィルティングポイントでの土壌水分。
  * `sw::Float64`: ウィルティングポイントでの土壌水分。
  * `sstar::Float64`: 土壌水分がフィールドキャパシティを下回るときの値。
  * `ks::Float64`: 飽和水力伝導率。
  * `β::Float64`: 水力伝導率曲線の指数。
  * `n::Float64`: 土壌の空隙率。
  * `zr::Float64`: 根の深さ。
  * `cws::Float64`: キャノピー水貯蔵容量。
  * `ce::Float64`: 基準蒸発係数。
  * `ct::Float64`: 基準蒸散係数。
  * `dt::Float64`: 時間間隔。
