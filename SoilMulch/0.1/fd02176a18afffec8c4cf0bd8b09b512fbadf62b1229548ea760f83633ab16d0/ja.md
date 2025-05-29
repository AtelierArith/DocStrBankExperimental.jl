`soil_mulch_water_balance(rain, eto, cf, ϑ, s, sh, sw, sstar, ks, β, n, zr, cws,                           ce, ct, μ, ϕ, zm, ϑh, km, g, dt)`

マルチングと土壌水分バランスを計算します。

# 引数

  * `rain::Float64`: 降雨量。
  * `eto::Float64`: 参照蒸発散。
  * `cf::Float64`: 作物被覆率。
  * `ϑ::Float64`: マルチング水分。
  * `s::Float64`: 土壌水分。
  * `sh::Float64`: ウィルティングポイントでの土壌水分。
  * `sw::Float64`: ウィルティングポイントでの土壌水分。
  * `sstar::Float64`: 土壌水分がフィールド容量を下回るとき。
  * `ks::Float64`: 飽和水力伝導率。
  * `β::Float64`: 水力伝導曲線の指数。
  * `n::Float64`: 土壌の空隙率。
  * `zr::Float64`: 根の深さ。
  * `cws::Float64`: キャノピー水貯蔵容量。
  * `ce::Float64`: 基準蒸発係数。
  * `ct::Float64`: 基準蒸散係数。
  * `ϕ::Float64`: マルチングの空隙率。
  * `ϑh::Float64`: マルチの漏出と蒸発を停止させる閾値。
  * `km::Float64`: マルチングの浸透率。
  * `g::Float64`: マルチング浸透の指数。
  * `dt::Float64`: 時間間隔。
