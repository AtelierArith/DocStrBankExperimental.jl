```
MCLResult <: ClusteringResult
```

[`mcl`](@ref) 関数の出力。

# フィールド

  * `mcl_adj::AbstractMatrix`: 最終的な MCL 隣接行列（アルゴリズムが収束した場合の平衡状態行列）、`save_final_matrix` オプションが無効の場合は空
  * `assignments::Vector{Int}`: ポイントクラスタのインデックス。`assignments[i]` は $i$-番目のポイントのクラスタのインデックス（未割り当ての場合は $0$）
  * `counts::Vector{Int}`: クラスタサイズの $k$-長ベクトル
  * `nunassigned::Int`: どのクラスタにも割り当てられていないスタンドアロンポイントの数
  * `iterations::Int`: 経過したイテレーションの数
  * `rel_Δ::Float64`: 最終的な相対 Δ
  * `converged::Bool`: メソッドが収束したかどうか
