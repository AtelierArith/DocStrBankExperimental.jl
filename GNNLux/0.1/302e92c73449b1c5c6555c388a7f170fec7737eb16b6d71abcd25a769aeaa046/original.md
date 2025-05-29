```
SAGEConv(in => out, σ=identity; aggr=mean, init_weight = glorot_uniform, init_bias = zeros32, use_bias=true)
```

GraphSAGE convolution layer from paper [Inductive Representation Learning on Large Graphs](https://arxiv.org/pdf/1706.02216.pdf).

Performs:

$$
\mathbf{x}_i' = W \cdot [\mathbf{x}_i; \square_{j \in \mathcal{N}(i)} \mathbf{x}_j]
$$

where the aggregation type is selected by `aggr`.

# Arguments

  * `in`: The dimension of input features.
  * `out`: The dimension of output features.
  * `σ`: Activation function.
  * `aggr`: Aggregation operator for the incoming messages (e.g. `+`, `*`, `max`, `min`, and `mean`).
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
x = rand(rng, Float32, in_channel, g.num_nodes)

# create layer
l = SAGEConv(in_channel => out_channel, tanh, use_bias = false, aggr = +)

# setup layer
ps, st = LuxCore.setup(rng, l)

# forward pass
y, st = l(g, x, ps, st)       # size:  out_channel × num_nodes   
```
