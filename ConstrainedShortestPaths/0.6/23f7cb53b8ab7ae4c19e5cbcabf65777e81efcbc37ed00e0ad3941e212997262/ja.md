```julia
stochastic_routing_shortest_path(
    graph::Graphs.AbstractGraph{T},
    slacks::AbstractMatrix,
    intrinsic_delays::AbstractMatrix;
    ...
) -> Union{NamedTuple{(:p_star, :c_star, :info, :bounds), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_bounds::Int64, nb_cuts_with_dominance::Int64}, Dict{Int64}}}, NamedTuple{(:p_star, :c_star, :info), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_dominance::Int64}}}}
stochastic_routing_shortest_path(
    graph::Graphs.AbstractGraph{T},
    slacks::AbstractMatrix,
    intrinsic_delays::AbstractMatrix,
    λ_values::AbstractVector;
    origin_vertex,
    destination_vertex,
    bounding,
    use_convex_resources
) -> Union{NamedTuple{(:p_star, :c_star, :info, :bounds), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_bounds::Int64, nb_cuts_with_dominance::Int64}, Dict{Int64}}}, NamedTuple{(:p_star, :c_star, :info), <:Tuple{Vector, Any, @NamedTuple{nb_cuts_with_dominance::Int64}}}}

```

`graph`の`origin_vertex`と`destination_vertex`の間の確率的ルーティング最短経路を計算します。

# 引数

  * `graph::AbstractGraph`: 非循環有向グラフ。
  * `slacks`: `slacks[i, j]`は`i`と`j`の間の時間の余裕を表します。
  * `delays`: `delays[i, ω]`はシナリオ`ω`に対する`i`の遅延を表します。

# 戻り値

  * `p_star::Vector{Int}`: 見つかった最適経路。
  * `c_star::Float64`: 経路`p_star`の長さ。
