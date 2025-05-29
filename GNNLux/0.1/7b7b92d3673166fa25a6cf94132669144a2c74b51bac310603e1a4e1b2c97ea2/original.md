```
DConv(in => out, k; init_weight = glorot_uniform, init_bias = zeros32, use_bias = true)
```

Diffusion convolution layer from the paper [Diffusion Convolutional Recurrent Neural Networks: Data-Driven Traffic Forecasting](https://arxiv.org/pdf/1707.01926).

# Arguments

  * `in`: The dimension of input features.
  * `out`: The dimension of output features.
  * `k`: Number of diffusion steps.
  * `init_weight`: Weights' initializer. Default `glorot_uniform`.
  * `init_bias`: Bias initializer. Default `zeros32`.
  * `use_bias`: Add learnable bias. Default `true`.

# Examples

```julia
using GNNLux, Lux, Random

# initialize random number generator
rng = Random.default_rng()

# create random graph
g = GNNGraph(rand(rng, 10, 10), ndata = rand(rng, Float32, 2, 10))

dconv = DConv(2 => 4, 4)

# setup layer
ps, st = LuxCore.setup(rng, dconv)

# forward pass
y, st = dconv(g, g.ndata.x, ps, st)   # size: (4, num_nodes)
```
