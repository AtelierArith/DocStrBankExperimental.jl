```
props = calculate_properties(fluid, T, P, verbose=true)
```

状態方程式を使用して、与えられた温度と圧力での実流体の密度、ファガシティ、およびモル体積を計算します。

# 引数

  * `fluid::Union{PengRobinsonFluid, VdWFluid}`: ペン-ロビンソン/ファン・デル・ワールス流体データ構造
  * `T::Float64`: 温度（単位：ケルビン）
  * `P::Float64`: 圧力（単位：バール）
  * `verbose::Bool`: `true`の場合、結果を出力します

# 戻り値

  * `prop_dict::Dict`: ペン-ロビンソン/ファン・デル・ワールス流体の特性の辞書
