```
adjacency([a,data])
```

隣接オブジェクトを構築します。`a` が `AbstractMatrix`、`AbstractGraph`、または `Tuple` の場合、使用可能な隣接関係を返します。`a` が `Function` または `PartialAdjacency` の場合、`data` が存在する必要があります。両方の引数が欠けている場合、関数は `EmptyAdjacency` を返します。

# 例

```
julia> using NetworkLearning, LightGraphs

julia> A = [0 1 0; 1 0 0; 0 0 0];

julia> Am = adjacency(A)
Matrix adjacency, 3 obs

julia> Ag = adjacency(Graph(A))
Graph adjacency, 3 obs

julia> Ac = adjacency(x->x,A)
Computable adjacency
```
