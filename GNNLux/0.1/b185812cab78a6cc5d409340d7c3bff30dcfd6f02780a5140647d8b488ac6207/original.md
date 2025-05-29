```
CGConv((in, ein) => out, act = identity; residual = false,
            use_bias = true, init_weight = glorot_uniform, init_bias = zeros32)
CGConv(in => out, ...)
```

The crystal graph convolutional layer from the paper [Crystal Graph Convolutional Neural Networks for an Accurate and Interpretable Prediction of Material Properties](https://arxiv.org/pdf/1710.10324.pdf). Performs the operation

$$
\mathbf{x}_i' = \mathbf{x}_i + \sum_{j\in N(i)}\sigma(W_f \mathbf{z}_{ij} + \mathbf{b}_f)\, act(W_s \mathbf{z}_{ij} + \mathbf{b}_s)
$$

where $\mathbf{z}_{ij}$  is the node and edge features concatenation  $[\mathbf{x}_i; \mathbf{x}_j; \mathbf{e}_{j\to i}]$  and $\sigma$ is the sigmoid function. The residual $\mathbf{x}_i$ is added only if `residual=true` and the output size is the same  as the input size.

# Arguments

  * `in`: The dimension of input node features.
  * `ein`: The dimension of input edge features.

If `ein` is not given, assumes that no edge features are passed as input in the forward pass.

  * `out`: The dimension of output node features.
  * `act`: Activation function.
  * `residual`: Add a residual connection.
  * `init_weight`: Weights' initializer. Default `glorot_uniform`.
  * `init_bias`: Bias initializer. Default `zeros32`.
  * `use_bias`: Add learnable bias. Default `true`.

# Examples

```julia
using GNNLux, Lux, Random

# initialize random number generator
rng = Random.default_rng()

# create random graph
g = rand_graph(rng, 5, 6)
x = rand(rng, Float32, 2, g.num_nodes)
e = rand(rng, Float32, 3, g.num_edges)

l = CGConv((2, 3) => 4, tanh)

# setup layer
ps, st = LuxCore.setup(rng, l)

# forward pass
y, st = l(g, x, e, ps, st)    # size: (4, num_nodes)

# No edge features
l = CGConv(2 => 4, tanh)
ps, st = LuxCore.setup(rng, l)
y, st = l(g, x, ps, st)    # size: (4, num_nodes)
```
