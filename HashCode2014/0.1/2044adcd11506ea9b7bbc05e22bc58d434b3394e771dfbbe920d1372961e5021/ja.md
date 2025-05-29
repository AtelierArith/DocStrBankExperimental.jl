```
都市
```

[`Junction`](@ref)と[`Street`](@ref)で構成される都市を、追加のインスタンスパラメータと共に保存します。

# フィールド

  * `total_duration::Int`: 車の旅程に割り当てられた総時間（秒単位）
  * `nb_cars::Int`: フリート内の車の数
  * `starting_junction::Int`: すべての車が最初に位置するジャンクション
  * `junctions::Vector{Junction}`: ジャンクションのリスト
  * `streets::Vector{Street}`: ストリートのリスト
