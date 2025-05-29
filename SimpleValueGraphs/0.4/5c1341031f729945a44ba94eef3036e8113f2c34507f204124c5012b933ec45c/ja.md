```
get_edgeval(g::AbstractValGraph, s, d, :)
```

グラフ `g` におけるエッジ `s -> d` に関連付けられたすべての値を返します。

そのようなエッジがグラフに存在しない場合は例外をスローします。

### 参照

[`get_edgeval_or`](@ref), [`set_edgeval!`](@ref)

### 例

```jldoctest
julia> gv = ValDiGraph(path_digraph(3), edgeval_types=(a=Float64, b=Int), edgeval_init=(s, d) -> (rand(MersenneTwister(0)), 10))
{3, 2} directed ValDiGraph with
              eltype: Int64
  vertex value types: ()
    edge value types: (a = Float64, b = Int64)
   graph value types: ()

julia> get_edgeval(gv, 1, 2, :)
(a = 0.8236475079774124, b = 10)

julia> get_edgeval(gv, 1, 3, :)
ERROR: Values not found
```
