```
SAGEConv(in => out, σ=identity; aggr=mean, bias=true, init=glorot_uniform)
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
  * `bias`: Add learnable bias.
  * `init`: Weights' initializer.

# Examples:

```julia
# create data
s = [1,1,2,3]
t = [2,3,1,1]
in_channel = 3
out_channel = 5
g = GNNGraph(s, t)

# create layer
l = SAGEConv(in_channel => out_channel, tanh, bias = false, aggr = +)

# forward pass
y = l(g, x)   
```
