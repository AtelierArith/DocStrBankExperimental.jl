```
deployment_area(n_corals::Int64, max_n_corals::Int64, density::Float64, target_areas::Vector{Float64})::Tuple{Float64,Float64}
```

期待されるサンゴの数を展開するための展開面積を決定します。

# 引数

  * `n_corals` : サンゴの数、
  * `max_n_corals` : 予想される最大展開努力（介入セット内のサンゴの総数）
  * `density` : m²あたりのストッキング密度
  * `target_areas` : 目標地点での利用可能面積

# 戻り値

タプル

  * 展開面積のパーセント
  * 修正されたストッキング密度 [現在は修正は行われていません]
