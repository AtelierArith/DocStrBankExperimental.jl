```
get_edgeval(g::AbstractValGraph, s, d, key)
```

グラフ `g` において、キー `key` に関連付けられたエッジ `s -> d` の値を返します。

グラフにそのようなエッジが存在しない場合や、キーが有効なエッジキーでない場合は例外をスローします。

エッジごとに1つの値しか持たないグラフの場合、`key` は省略できます。

### 参照

[`get_edgeval_or`](@ref), [`set_edgeval!`](@ref)

### 例

```jldoctest
julia> gv = ValDiGraph(path_digraph(3), edgeval_types=(a=Float64,), edgeval_init=(s, d) -> (rand(MersenneTwister(0)),))
{3, 2} directed ValDiGraph with
              eltype: Int64
  vertex value types: ()
    edge value types: (a = Float64,)
   graph value types: ()

julia> get_edgeval(gv, 1, 2, :a)
0.8236475079774124

julia> get_edgeval(gv, 1, 2, 1)
0.8236475079774124

julia> get_edgeval(gv, 1, 2)
0.8236475079774124

julia> get_edgeval(gv, 1, 3)
ERROR: No such edge

julia> get_edgeval(gv, 1, 2, :b)
ERROR: b is not a valid edge key for this graph.
```
