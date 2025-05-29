GraphProperties

[`DAG`](@ref)のプロパティの表現。

## フィールド:

  * `data::Float64`: 総データ転送量。
  * `compute_effort::Float64`: 総計算努力。
  * `compute_intensity::Float64`: 計算強度、常に `compute_effort / data` に等しい。
  * `number_of_nodes::Int`: [`Node`](@ref)の数。
  * `number_of_edges::Int`: [`Edge`](@ref)の数。
