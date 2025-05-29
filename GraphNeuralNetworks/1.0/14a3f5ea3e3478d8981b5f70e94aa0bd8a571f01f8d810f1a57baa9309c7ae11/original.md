```
NNConv(in => out, f, σ=identity; aggr=+, bias=true, init=glorot_uniform)
```

The continuous kernel-based convolutional operator from the  [Neural Message Passing for Quantum Chemistry](https://arxiv.org/abs/1704.01212) paper.  This convolution is also known as the edge-conditioned convolution from the  [Dynamic Edge-Conditioned Filters in Convolutional Neural Networks on Graphs](https://arxiv.org/abs/1704.02901) paper.

Performs the operation

$$
\mathbf{x}_i' = W \mathbf{x}_i + \square_{j \in N(i)} f_\Theta(\mathbf{e}_{j\to i})\,\mathbf{x}_j
$$

where $f_\Theta$  denotes a learnable function (e.g. a linear layer or a multi-layer perceptron). Given an input of batched edge features `e` of size `(num_edge_features, num_edges)`,  the function `f` will return an batched matrices array whose size is `(out, in, num_edges)`. For convenience, also functions returning a single `(out*in, num_edges)` matrix are allowed.

# Arguments

  * `in`: The dimension of input node features.
  * `out`: The dimension of output node features.
  * `f`: A (possibly learnable) function acting on edge features.
  * `aggr`: Aggregation operator for the incoming messages (e.g. `+`, `*`, `max`, `min`, and `mean`).
  * `σ`: Activation function.
  * `bias`: Add learnable bias.
  * `init`: Weights' initializer.

# Examples:

```julia
n_in = 3
n_in_edge = 10
n_out = 5

# create data
s = [1,1,2,3]
t = [2,3,1,1]
g = GNNGraph(s, t)

# create dense layer
nn = Dense(n_in_edge => n_out * n_in)

# create layer
l = NNConv(n_in => n_out, nn, tanh, bias = true, aggr = +)

x = randn(Float32, n_in, g.num_nodes)
e = randn(Float32, n_in_edge, g.num_edges)

# forward pass
y = l(g, x, e)  
```
