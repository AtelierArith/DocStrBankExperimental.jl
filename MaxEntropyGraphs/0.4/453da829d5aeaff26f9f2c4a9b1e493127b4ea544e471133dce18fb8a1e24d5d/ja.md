```
project(G::Graphs.SimpleGraph;  membership::Vector=Graphs.bipartite_map(G), 
                                bottom::Vector=findall(membership .== 1), 
                                top::Vector=findall(membership .== 2); 
                                layer::Symbol=:bottom)
```

二部グラフ `G` をその層の一つに射影し、射影されたグラフを返します。

# 引数

  * `membership`: グラフの二部マッピング。これは `Graphs.bipartite_map(G)` を使用して計算できます。
  * `bottom`: 下層のノード。これは `findall(membership .== 1)` を使用して計算できます。
  * `top`: 上層のノード。これは `findall(membership .== 2)` を使用して計算できます。
  * `layer`: 層は `layer=:bottom` または `layer=:top` を渡すことで指定できます。層のメンバーシップはグラフの二部マップによって決定されます。
  * `method`: 射影されたグラフの隣接行列を計算するために使用される方法。この方法は `:simple` または `:weighted` です。両方の方法は二重隣接行列とその転置の積を計算しますが、`:weighted` 方法は射影されたグラフのエッジの重みを使用します。

# 例

```jldoctest project_bipartite_to_simple
julia> using Graphs

julia> G = SimpleGraph(5); add_edge!(G, 1, 4); add_edge!(G, 2, 4); add_edge!(G, 3, 4); add_edge!(G, 3, 5);

julia> project(G, layer=:bottom)
{3, 3} undirected simple Int64 graph

```

```jldoctest project_bipartite_to_simple
julia> project(G, layer=:top)
{2, 1} undirected simple Int64 graph

```
