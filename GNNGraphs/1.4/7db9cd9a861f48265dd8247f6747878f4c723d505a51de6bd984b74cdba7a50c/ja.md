```
rand_bipartite_heterograph([rng,] 
                           (n1, n2), (m12, m21); 
                           bidirected = true, 
                           node_t = (:A, :B), 
                           edge_t = :to, 
                           kws...)
```

ランダムなエッジを持つ二部グラフを表す[`GNNHeteroGraph`](@ref)を構築します。このグラフには2種類のノードがあり、エッジは異なるタイプのノードのみを接続します。

最初の引数はタプル`(n1, n2)`で、各タイプのノードの数を指定します。2番目の引数はタプル`(m12, m21)`で、タイプ`1`のノードからタイプ`2`のノードへのエッジの数とその逆を指定します。

ノードとエッジのタイプは、デフォルトで`(:A, :B)`および`:to`のキーワード引数`node_t`と`edge_t`を使用して指定できます。

`bidirected=true`（デフォルト）の場合、各エッジの逆エッジも存在します。この場合、`m12 == m21`が必要です。

生成を再現可能にするために、最初の引数としてランダム数生成器を渡すことができます。

追加のキーワード引数は、[`GNNHeteroGraph`](@ref)コンストラクタに渡されます。

より一般的なバージョンについては、[`rand_heterograph`](@ref)を参照してください。

# 例

```julia
julia> g = rand_bipartite_heterograph((10, 15), 20)
GNNHeteroGraph:
  num_nodes: (:A => 10, :B => 15)
  num_edges: ((:A, :to, :B) => 20, (:B, :to, :A) => 20)

julia> g = rand_bipartite_heterograph((10, 15), (20, 0), node_t=(:user, :item), edge_t=:-, bidirected=false)
GNNHeteroGraph:
  num_nodes: Dict(:item => 15, :user => 10)
  num_edges: Dict((:item, :-, :user) => 0, (:user, :-, :item) => 20)
```
