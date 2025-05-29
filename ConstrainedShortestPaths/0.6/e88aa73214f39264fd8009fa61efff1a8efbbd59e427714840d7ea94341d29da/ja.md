```julia
resource_shortest_path(
    graph::Graphs.AbstractGraph{T},
    s,
    t,
    max_costs::AbstractVector,
    distmx::AbstractMatrix,
    costmx::Array{Float64, 3};
    bounding
) -> Union{NamedTuple{(:p_star, :c_star, :info, :bounds), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_bounds::Int64, nb_cuts_with_dominance::Int64}, Dict{Int64}}}, NamedTuple{(:p_star, :c_star, :info), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_dominance::Int64}}}}

```

頂点 `s` と `t` の間のリソース制約付き最短経路をグラフ `g` に対して計算します。

# 引数

  * `g::AbstractGraph`: 非循環有向グラフ。
  * `max_costs::AbstractVector`: 各リソース制約の上限のリスト。
  * `distmx::AbstractMatrix`: `distmx[i, j]` は、グラフ `g` の辺 `(i, j)` に沿った頂点 `i` と `j` の間の距離に対応します。
  * `costmx::Array{Float64, 3}`: `cost_mx[i, j, k]` は、`k` 番目のリソース制約に対する辺 `(i, j)` のリソースコストに対応します。

# 戻り値

  * `p_star::Vector{Int}`: 見つかった最適経路。
  * `c_star::Float64`: 経路 `p_star` の長さ。
