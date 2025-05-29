"     SurvivalMetric <: AbstractMetric

## フィールド

  * `size::Int`: データセットのサイズ。
  * `levels::Vector{Float64}`: サバイバルレベル（例: 0.9, 0.8, 0.7）。
  * `values::Vector{Float64}`: サバイバルレベルに対応する値。
  * `cov_inv::Matrix{Float64}`: グループの共分散行列の逆行列。
  * `group_active::Vector{Bool}`: どのグループがアクティブ（非ゼロ率）であるかを示すブールベクトル。
  * `rates::Vector{Float64}`: 各グループの確率。

## コンストラクタ

  * `SurvivalMetric(size::Int, levels::Vector{Float64}, values::Vector{Float64})`: SurvivalMetricの新しいインスタンスを作成します。入力データを検証し、逆共分散行列を計算します。
