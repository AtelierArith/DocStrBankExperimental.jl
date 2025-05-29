```
set_outplant_deployment!(name::String, reefset::String, n_corals::Int64, max_effort::Int64, first_year::Int64, last_year::Int64, year_step::Int64, area_km2::Vector{Float64}, density::Float64)::Nothing
```

出植えの展開を一連の年にわたって設定します。

# 引数

  * `name` : 介入イベントに割り当てる名前
  * `reefset` : 介入するための事前定義されたサンゴ礁のリストの名前
  * `n_corals` : 特定の年に出植えするサンゴの数
  * `max_effort` : 出植えするサンゴの総数
  * `first_year` : 介入を開始する最初の年
  * `last_year` : 介入の最終年
  * `year_step` : 介入の頻度 (1 = 毎年, 2 = 2年ごと, など)
  * `area_km2` : 介入面積 [km²]
  * `density` : 介入のストッキング密度 [サンゴ / m²]
