指定されたタイプによるネットワークのモデルを確立します。

# 引数

  * `::Type{T}`: PowerModels AbstractPowerModel

# 受け入れられるキーワード

  * `use_slacks::Bool`: ネットワークモデリングにスラックを追加します
  * `PTDF::PTDF`: PowerNetworkMatricesを使用して計算されたPTDF配列
  * `duals::Vector{DataType}`: 双対を計算するための制約タイプ
  * `reduce_radial_branches::Bool`: 問題のサイズを減らすためにシステム内の放射状ブランチのモデリングをスキップします

# 例

ptdf*array = PTDF(system) nw = NetworkModel(PTDFPowerModel, ptdf = ptdf*array),
