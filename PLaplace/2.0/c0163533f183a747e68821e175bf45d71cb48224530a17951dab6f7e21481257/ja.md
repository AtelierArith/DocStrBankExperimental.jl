```
compute_prolongation_harmonic(
    g::AbstractVector{Float64},
    mesh::Mesh,
    has_sourceterm::Bool,
    f::AbstractVector{Float64}, 
    dirichlet_nodes::Set{Int64},
    has_neumannboundary::Bool,
    h::AbstractVector{Float64},
    neumann_elements::Set{Int64}, 
    solveLS::Function,
    preconditioner::Function;
    qdim::Int64 = 1
) -> AbstractVector{Float64}
```

境界条件 g の離散的な延長を全領域に返し、対応する線形ラプラス問題の解として、すなわち $p = 2$。

# 必須引数

  * `g::AbstractVector{Float64}`: 離散的に評価された境界条件。
  * `mesh::Mesh`: 領域のメッシュ。
  * `has_sourceterm::Bool`: ソース項を評価するためのフラグ。
  * `f::AbstractVector{Float64}`: ソース項。
  * `dirichlet_nodes::Set{Int64}`: ディリクレ条件を保持する境界のノード。
  * `has_neumannboundary::Bool`: ノイマン境界を評価するためのフラグ。
  * `h::AbstractVector{Float64}`: ノイマン境界条件。
  * `neumann_elements::Set{Int64}`: ノイマン条件を保持する境界のエッジ。
  * `solveLS::Function`: 線形システムを解くための関数ポインタ。
  * `preconditioner::Function`: 線形システムの前処理器を計算するための関数ポインタ。

# キーワード引数

  * `qdim::Int64 = 1`: f, h, および g の成分数。
