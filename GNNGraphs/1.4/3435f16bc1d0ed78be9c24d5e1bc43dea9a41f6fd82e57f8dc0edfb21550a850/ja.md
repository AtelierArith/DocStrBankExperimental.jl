```
rand_heterograph([rng,] n, m; bidirected=false, kws...)
```

指定されたノード数 `n` とエッジ数 `m` を持つランダムエッジの [`GNNHeteroGraph`](@ref) を構築します。 `n` と `m` は、ノード/エッジタイプとその数を指定する任意のペアのイテラブルであることができます。

生成を再現可能にするために、最初の引数としてランダム数生成器を渡します。

`bidirected=true` を設定すると、双方向グラフが生成されます。つまり、各エッジには逆エッジがあります。したがって、各エッジタイプ `(:A, :rel, :B)` に対して、対応する逆エッジタイプ `(:B, :rel, :A)` が生成されます。

追加のキーワード引数は、[`GNNHeteroGraph`](@ref) コンストラクタに渡されます。

# 例

```jldoctest
julia> g = rand_heterograph((:user => 10, :movie => 20),
                            (:user, :rate, :movie) => 30)
GNNHeteroGraph:
  num_nodes: Dict(:movie => 20, :user => 10)
  num_edges: Dict((:user, :rate, :movie) => 30)
```
