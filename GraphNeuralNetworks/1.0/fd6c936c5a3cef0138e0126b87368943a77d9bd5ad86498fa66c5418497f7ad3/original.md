```
GlobalAttentionPool(fgate, ffeat=identity)
```

Global soft attention layer from the [Gated Graph Sequence Neural Networks](https://arxiv.org/abs/1511.05493) paper

$$
\mathbf{u}_V = \sum_{i\in V} \alpha_i\, f_{feat}(\mathbf{x}_i)
$$

where the coefficients $\alpha_i$ are given by a [`softmax_nodes`](@ref) operation:

$$
\alpha_i = \frac{e^{f_{gate}(\mathbf{x}_i)}}
                {\sum_{i'\in V} e^{f_{gate}(\mathbf{x}_{i'})}}.
$$

# Arguments

  * `fgate`: The function $f_{gate}: \mathbb{R}^{D_{in}} \to \mathbb{R}$.           It is tipically expressed by a neural network.
  * `ffeat`: The function $f_{feat}: \mathbb{R}^{D_{in}} \to \mathbb{R}^{D_{out}}$.           It is tipically expressed by a neural network.

# Examples

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
