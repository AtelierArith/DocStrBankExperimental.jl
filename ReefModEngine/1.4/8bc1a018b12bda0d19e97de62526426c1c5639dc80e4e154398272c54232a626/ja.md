```
set_outplant_deployment!(name::String, reefset::String, n_corals::Int64, year::Int64, area_km2::Vector{Float64})::Nothing
```

単一の年のためのアウトプランティング展開を設定し、設定されたグリッドサイズを維持するためにサンゴの展開密度を自動的に決定します。

# 引数

  * `name` : 介入イベントに割り当てる名前
  * `reefset` : 介入するための事前定義されたサンゴ礁のリストの名前
  * `n_corals` : アウトプランティングするサンゴの数
  * `year` : 介入する年
  * `area_km2` : 介入する面積 [km²]
