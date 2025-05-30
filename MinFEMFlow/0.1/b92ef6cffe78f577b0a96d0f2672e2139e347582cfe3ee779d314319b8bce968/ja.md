```julia
mutable struct FlowSolver
```

反復中に静的なデータをすべて保存します。対応するコンストラクタによって生成されることになっています。

# フィールド

  * `mesh::MinFEM.Mesh`: メッシュ化された計算領域
  * `inflow_boundary::Set{Int64}`: 指定されたディリクレ速度を持つ流入境界
  * `noslip_boundary::Set{Int64}`: 指定されたディリクレ値を持つノースリップ境界
  * `inflow::Vector{Float64}`: 流入速度関数
  * `verbose::Bool`: 解決中の出力を書き込むためのスイッチ
  * `solve::Function`: 流れのタイプを本質的に決定する流れの解決ルーチン
  * `v::Union{Missing, Vector{Float64}}`: 結果として得られる速度場
  * `p::Union{Missing, Vector{Float64}}`: 結果として得られる圧力
  * `time::Union{Missing, Float64}`: 必要な解決時間、結果が存在するかどうかを検証するためのもの
