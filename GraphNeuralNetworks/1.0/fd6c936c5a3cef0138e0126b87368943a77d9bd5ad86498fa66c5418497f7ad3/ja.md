```
GlobalAttentionPool(fgate, ffeat=identity)
```

[Gated Graph Sequence Neural Networks](https://arxiv.org/abs/1511.05493) 論文からのグローバルソフトアテンション層

$$
\mathbf{u}_V = \sum_{i\in V} \alpha_i\, f_{feat}(\mathbf{x}_i)
$$

ここで、係数 $\alpha_i$ は [`softmax_nodes`](@ref) 操作によって与えられます：

$$
\alpha_i = \frac{e^{f_{gate}(\mathbf{x}_i)}}
                {\sum_{i'\in V} e^{f_{gate}(\mathbf{x}_{i'})}}.
$$

# 引数

  * `fgate`: 関数 $f_{gate}: \mathbb{R}^{D_{in}} \to \mathbb{R}$。           通常はニューラルネットワークによって表現されます。
  * `ffeat`: 関数 $f_{feat}: \mathbb{R}^{D_{in}} \to \mathbb{R}^{D_{out}}$。           通常はニューラルネットワークによって表現されます。

# 例

```julia
chin = 6
chout = 5    

fgate = Dense(chin, 1)
ffeat = Dense(chin, chout)
pool = GlobalAttentionPool(fgate, ffeat)

g = Flux.batch([GNNGraph(random_regular_graph(10, 4), 
                         ndata=rand(Float32, chin, 10)) 
                for i=1:3])

u = pool(g, g.ndata.x)

@assert size(u) == (chout, g.num_graphs)
```
