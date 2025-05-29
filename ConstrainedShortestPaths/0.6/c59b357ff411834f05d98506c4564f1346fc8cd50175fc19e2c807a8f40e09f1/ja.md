```julia
basic_shortest_path(
    graph::Graphs.AbstractGraph{T},
    s,
    t;
    ...
) -> Union{NamedTuple{(:p_star, :c_star, :info, :bounds), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_bounds::Int64, nb_cuts_with_dominance::Int64}, Dict{Int64}}}, NamedTuple{(:p_star, :c_star, :info), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_dominance::Int64}}}}
basic_shortest_path(
    graph::Graphs.AbstractGraph{T},
    s,
    t,
    distmx::AbstractMatrix;
    bounding
) -> Union{NamedTuple{(:p_star, :c_star, :info, :bounds), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_bounds::Int64, nb_cuts_with_dominance::Int64}, Dict{Int64}}}, NamedTuple{(:p_star, :c_star, :info), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_dominance::Int64}}}}

```

グラフ `graph` の頂点 `s` と `t` の間の最短経路を計算します。

# 引数

  * `graph::AbstractGraph`: 非循環有向グラフ。
  * `distmx::AbstractMatrix`: `distmx[i, j]` は、グラフの辺 `(i, j)` に沿った頂点 `i` と `j` の間の距離に対応します。

# 戻り値

  * `p_star::Vector{Int}`: 見つかった最適経路。
  * `c_star::Float64`: 経路 `p_star` の長さ。
