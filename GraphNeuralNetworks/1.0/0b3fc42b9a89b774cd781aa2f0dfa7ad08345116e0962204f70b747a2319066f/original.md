```
GraphConv(in => out, σ=identity; aggr=+, bias=true, init=glorot_uniform)
```

Graph convolution layer from Reference: [Weisfeiler and Leman Go Neural: Higher-order Graph Neural Networks](https://arxiv.org/abs/1810.02244).

Performs:

$$
\mathbf{x}_i' = W_1 \mathbf{x}_i + \square_{j \in \mathcal{N}(i)} W_2 \mathbf{x}_j
$$

where the aggregation type is selected by `aggr`.

# Arguments

  * `in`: The dimension of input features.
  * `out`: The dimension of output features.
  * `σ`: Activation function.
  * `aggr`: Aggregation operator for the incoming messages (e.g. `+`, `*`, `max`, `min`, and `mean`).
  * `bias`: Add learnable bias.
  * `init`: Weights' initializer.

# Examples

```julia
# create data
s = [1,1,2,3]
t = [2,3,1,1]
in_channel = 3
out_channel = 5
g = GNNGraph(s, t)
x = randn(Float32, 3, g.num_nodes)

# create layer
l = GraphConv(in_channel => out_channel, relu, bias = false, aggr = mean)

# forward pass
y = l(g, x)       
```
