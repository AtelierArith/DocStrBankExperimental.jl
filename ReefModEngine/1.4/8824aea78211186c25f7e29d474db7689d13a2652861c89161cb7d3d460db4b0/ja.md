```
set_outplant_deployment!(name::String, reefset::String, n_corals::Int64, year::Int64, area_km2::Vector{Float64}, density::Float64)::Nothing
```

単一の年のためのアウトプランティング展開を設定します。

# 引数

  * `name` : 介入イベントに割り当てる名前
  * `reefset` : 介入するための事前定義されたサンゴ礁のリストの名前
  * `n_corals` : アウトプランティングするサンゴの数
  * `year` : 介入する年
  * `area_km2` : 介入する面積 [km²]
  * `density` : 介入のストッキング密度 [サンゴ / m²]
