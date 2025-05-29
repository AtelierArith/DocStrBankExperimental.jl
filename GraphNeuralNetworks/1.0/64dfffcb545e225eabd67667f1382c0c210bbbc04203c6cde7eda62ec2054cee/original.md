```
GatedGraphConv(out, num_layers; aggr=+, init=glorot_uniform)
```

Gated graph convolution layer from [Gated Graph Sequence Neural Networks](https://arxiv.org/abs/1511.05493).

Implements the recursion

$$
\begin{aligned}
\mathbf{h}^{(0)}_i &= [\mathbf{x}_i; \mathbf{0}] \\
\mathbf{h}^{(l)}_i &= GRU(\mathbf{h}^{(l-1)}_i, \square_{j \in N(i)} W \mathbf{h}^{(l-1)}_j)
\end{aligned}
$$

where $\mathbf{h}^{(l)}_i$ denotes the $l$-th hidden variables passing through GRU. The dimension of input $\mathbf{x}_i$ needs to be less or equal to `out`.

# Arguments

  * `out`: The dimension of output features.
  * `num_layers`: The number of recursion steps.
  * `aggr`: Aggregation operator for the incoming messages (e.g. `+`, `*`, `max`, `min`, and `mean`).
  * `init`: Weight initialization function.

# Examples:

```julia
# create data
s = [1,1,2,3]
t = [2,3,1,1]
out_channel = 5
num_layers = 3
g = GNNGraph(s, t)

# create layer
l = GatedGraphConv(out_channel, num_layers)

# forward pass
y = l(g, x)   
```
