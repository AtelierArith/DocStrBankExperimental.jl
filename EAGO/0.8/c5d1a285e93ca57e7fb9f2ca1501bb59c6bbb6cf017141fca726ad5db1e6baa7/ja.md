```julia
struct NodeBB
```

ブランチ・アンド・バウンドツリー内の各ノードに関連付けられた情報を格納します。

  * `lower_variable_bounds::Vector{Float64}`: 変数ボックスの下限。
  * `upper_variable_bounds::Vector{Float64}`: 変数ボックスの上限。
  * `is_integer::BitVector`: 次元が整数値かどうか
  * `continuous::Bool`: すべての次元が連続（または固定）であるかどうか
  * `lower_bound::Float64`: nodeBBにおける問題解の下限
  * `upper_bound::Float64`: nodeBBにおける問題解の上限
  * `depth::Int64`: B&Bツリーにおけるノードの深さ。
  * `cont_depth::Int64`: 連続値であったB&Bツリー内の最初の親の深さ
  * `id::Int64`: 各ノードのユニークID。
  * `branch_direction::EAGO.BranchDirection`: 最後のブランチが方向的に負か正か
  * `last_branch::Int64`: 最後のブランチの次元
  * `branch_extent::Float64`: 最後のブランチの範囲（擬似コスト計算に使用）
