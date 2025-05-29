```
GlobalPool(aggr)
```

グラフニューラルネットワークのためのグローバルプーリング層。グラフと特徴ノードを入力として受け取り、次の操作を実行します。

$$
\mathbf{u}_V = \square_{i \in V} \mathbf{x}_i
$$

ここで、$V$ は入力グラフのノードの集合であり、$\square$ で表される集約のタイプは `aggr` 引数によって選択されます。一般的に使用される集約は `mean`、`max`、および `+` です。

他にも [`reduce_nodes`](@ref) を参照してください。

# 例

```julia
using Flux, GraphNeuralNetworks, Graphs

pool = GlobalPool(mean)

g = GNNGraph(erdos_renyi(10, 4))
X = rand(32, 10)
pool(g, X) # => 32x1 行列


g = Flux.batch([GNNGraph(erdos_renyi(10, 4)) for _ in 1:5])
X = rand(32, 50)
pool(g, X) # => 32x5 行列
```
