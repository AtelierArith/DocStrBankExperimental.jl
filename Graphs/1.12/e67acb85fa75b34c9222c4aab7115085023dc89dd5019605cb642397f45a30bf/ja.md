```
all_simple_paths(g, u, v; cutoff)  --> Graphs.SimplePathIterator
all_simple_paths(g, u, vs; cutoff) --> Graphs.SimplePathIterator
```

グラフ `g` におけるソース頂点 `u` からターゲット頂点 `v` またはターゲット頂点の iterable `vs` へのすべての [単純経路](https://en.wikipedia.org/wiki/Path_(graph_theory)#Walk,_trail,_and_path) を生成するイテレータを返します。単純経路は繰り返しのない頂点を持ちます。

イテレータの要素（すなわち経路）は `collect` または `iterate` を介して具現化できます。経路は深さ優先探索の順序で反復されます。

要求された経路のソースとターゲットの頂点が同一である場合、すなわち `u = v` の場合、長さゼロの経路 `[u]` がイテレートの中に含まれます。

## キーワード引数

最大経路長（すなわち、エッジの数）はキーワード引数 `cutoff` によって制限されます（デフォルトは `nv(g)-1`）。経路の長さが `cutoff` を超える場合、その経路は省略されます。

## 例

```jldoctest allsimplepaths; setup = :(using Graphs)
julia> g = complete_graph(4);

julia> spi = all_simple_paths(g, 1, 4)
SimplePathIterator{SimpleGraph{Int64}}(1 → 4)

julia> collect(spi)
5-element Vector{Vector{Int64}}:
 [1, 2, 3, 4]
 [1, 2, 4]
 [1, 3, 2, 4]
 [1, 3, 4]
 [1, 4]
```

指定されたカットオフ（ここでは 2 エッジ）以下の経路長に検索を制限できます：

```jldoctest allsimplepaths; setup = :(using Graphs)
julia> collect(all_simple_paths(g, 1, 4; cutoff=2))
3-element Vector{Vector{Int64}}:
 [1, 2, 4]
 [1, 3, 4]
 [1, 4]
```
