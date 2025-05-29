```
EdgeConv(nn; aggr=max)
```

Edge convolutional layer from paper [Dynamic Graph CNN for Learning on Point Clouds](https://arxiv.org/abs/1801.07829).

Performs the operation

$$
\mathbf{x}_i' = \square_{j \in N(i)}\, nn([\mathbf{x}_i; \mathbf{x}_j - \mathbf{x}_i])
$$

where `nn` generally denotes a learnable function, e.g. a linear layer or a multi-layer perceptron.

# Arguments

  * `nn`: A (possibly learnable) function.
  * `aggr`: Aggregation operator for the incoming messages (e.g. `+`, `*`, `max`, `min`, and `mean`).

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
l = EdgeConv(Dense(2 * in_channel, out_channel), aggr = +)

# setup layer
ps, st = LuxCore.setup(rng, l)

# forward pass
y, st = l(g, x, ps, st)
```
