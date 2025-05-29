```
ResGatedGraphConv(in => out, act=identity; init_weight = glorot_uniform, init_bias = zeros32, use_bias = true)
```

The residual gated graph convolutional operator from the [Residual Gated Graph ConvNets](https://arxiv.org/abs/1711.07553) paper.

The layer's forward pass is given by

$$
\mathbf{x}_i' = act\big(U\mathbf{x}_i + \sum_{j \in N(i)} \eta_{ij} V \mathbf{x}_j\big),
$$

where the edge gates $\eta_{ij}$ are given by

$$
\eta_{ij} = sigmoid(A\mathbf{x}_i + B\mathbf{x}_j).
$$

# Arguments

  * `in`: The dimension of input features.
  * `out`: The dimension of output features.
  * `act`: Activation function.
  * `init_weight`: Weights' initializer. Default `glorot_uniform`.
  * `init_bias`: Bias initializer. Default `zeros32`.
  * `use_bias`: Add learnable bias. Default `true`.

# Examples:

```julia
using GNNLux, Lux, Random

# initialize random number generator
rng = Random.default_rng()

# create data
s = [1,1,2,3]
t = [2,3,1,1]
in_channel = 3
out_channel = 5
g = GNNGraph(s, t)
x = randn(rng, Float32, in_channel, g.num_nodes)

# create layer
l = ResGatedGraphConv(in_channel => out_channel, tanh, use_bias = true)

# setup layer
ps, st = LuxCore.setup(rng, l)

# forward pass
y, st = l(g, x, ps, st)       # size:  out_channel × num_nodes  
```
