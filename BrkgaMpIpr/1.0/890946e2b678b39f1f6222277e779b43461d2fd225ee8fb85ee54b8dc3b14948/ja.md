```
function shake!(brkga_data::BrkgaData, intensity::Int64,
                shaking_type::ShakingType, population_index::Int64 = Inf64)
```

選択した集団でシェイキングを実行します。この手順は、エリートクロモソームに変更（シェイキング）を適用し、残りの集団を完全にリセットします。

# 引数

  * `intensity::Int64`: シェイキングの強度 (> 0);
  * [`shaking_type::ShakingType`](@ref ShakingType): `CHANGE` または `SWAP` のいずれかの移動;
  * `population_index::Int64`: シェイキングされる集団のインデックス。`population_index > num_independent_populations` の場合、すべての集団がシェイキングされます。

# 例外

  * `ErrorException`: [`initialize!`](@ref) が事前に呼び出されていない場合。
  * `ArgumentError`: `population_index < 1` または `intensity < 1` の場合。
