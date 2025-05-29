```
rand_graph([rng,] n, m; bidirected=true, edge_weight = nothing, kws...)
```

ノードが `n` でエッジが `m` のランダム (エルデシュ-レーニー) `GNNGraph` を生成します。

`bidirected=true` の場合、各エッジの逆エッジが存在します。`bidirected=false` の場合は、代わりに `m` の無関係なエッジが生成されます。いずれの場合も、出力グラフには自己ループや多重エッジは含まれません。

ベクトルを `edge_weight` として渡すことができます。その長さは、指向性の場合は `m` と等しく、双方向の場合は `m÷2` と等しくなければなりません。

生成を再現可能にするために、最初の引数として乱数生成器を渡します。

追加のキーワード引数は [`GNNGraph`](@ref) コンストラクタに渡されます。

# 例

```julia
julia> g = rand_graph(5, 4, bidirected=false)
GNNGraph:
  num_nodes: 5
  num_edges: 4

julia> edge_index(g)
([4, 3, 2, 1], [5, 4, 3, 2])

# 双方向の場合、必要に応じてエッジデータが逆エッジに複製されます。
julia> g = rand_graph(5, 4, edata=rand(Float32, 16, 2))
GNNGraph:
  num_nodes: 5
  num_edges: 4
  edata:
        e = 16×4 Matrix{Float32}

# 各エッジには逆があります
julia> edge_index(g)
([1, 1, 5, 3], [5, 3, 1, 1])
```
