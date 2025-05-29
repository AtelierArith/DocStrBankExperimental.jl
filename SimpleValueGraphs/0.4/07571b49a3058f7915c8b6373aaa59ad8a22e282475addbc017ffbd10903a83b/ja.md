```
ValMatrix(g::AbstractGraph, key, zero_value)
```

グラフ `g` のための新しい `ValMatrix` ビューを構築します。ここで、値は `key` で指定されたエッジの値です。グラフに存在しないエントリは、行列内で `zero_value` で表されます。

### 参照

[`AdjacencyMatrix`](@ref), [`adjacency_matrix`](@ref), [`weights`](@ref)

### 例

```jldoctest
julia> gv = ValDiGraph(path_digraph(3),  edgeval_types=(a=Float64, b=String), edgeval_init=(s, d) -> (rand(MersenneTwister(0)), "$s-$d"))
{3, 2} directed ValDiGraph with
              eltype: Int64
  vertex value types: ()
    edge value types: (a = Float64, b = String)
   graph value types: ()

julia> ValMatrix(gv, 1, 0.0)
3×3 ValMatrix{Float64, ValDiGraph{Int64, Tuple{}, NamedTuple{(:a, :b), Tuple{Float64, String}}, Tuple{}, Tuple{}, NamedTuple{(:a, :b), Tuple{Vector{Vector{Float64}}, Vector{Vector{String}}}}}, 1}:
 0.0  0.823648  0.0
 0.0  0.0       0.823648
 0.0  0.0       0.0

julia> ValMatrix(gv, :b, nothing)
3×3 ValMatrix{Union{Nothing, String}, ValDiGraph{Int64, Tuple{}, NamedTuple{(:a, :b), Tuple{Float64, String}}, Tuple{}, Tuple{}, NamedTuple{(:a, :b), Tuple{Vector{Vector{Float64}}, Vector{Vector{String}}}}}, :b}:
 nothing  "1-2"    nothing
 nothing  nothing  "2-3"
 nothing  nothing  nothing
```
