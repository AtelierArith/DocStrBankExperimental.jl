```
GATv2Conv(in => out, [σ; heads, concat, init, bias, negative_slope, add_self_loops])
GATv2Conv((in, ein) => out, ...)
```

GATv2 attentional layer from the paper [How Attentive are Graph Attention Networks?](https://arxiv.org/abs/2105.14491).

Implements the operation

$$
\mathbf{x}_i' = \sum_{j \in N(i) \cup \{i\}} \alpha_{ij} W_1 \mathbf{x}_j
$$

where the attention coefficients $\alpha_{ij}$ are given by

$$
\alpha_{ij} = \frac{1}{z_i} \exp(\mathbf{a}^T LeakyReLU(W_2 \mathbf{x}_i + W_1 \mathbf{x}_j))
$$

with $z_i$ a normalization factor.

In case `ein > 0` is given, edge features of dimension `ein` will be expected in the forward pass  and the attention coefficients will be calculated as  

$$
\alpha_{ij} = \frac{1}{z_i} \exp(\mathbf{a}^T LeakyReLU(W_3 \mathbf{e}_{j\to i} + W_2 \mathbf{x}_i + W_1 \mathbf{x}_j)).
$$

# Arguments

  * `in`: The dimension of input node features.
  * `ein`: The dimension of input edge features. Default 0 (i.e. no edge features passed in the forward).
  * `out`: The dimension of output node features.
  * `σ`: Activation function. Default `identity`.
  * `bias`: Learn the additive bias if true. Default `true`.
  * `heads`: Number attention heads. Default `1`.
  * `concat`: Concatenate layer output or not. If not, layer output is averaged over the heads. Default `true`.
  * `negative_slope`: The parameter of LeakyReLU.Default `0.2`.
  * `add_self_loops`: Add self loops to the graph before performing the convolution. Default `true`.
  * `dropout`: Dropout probability on the normalized attention coefficient. Default `0.0`.

# Examples

```julia
# create data
s = [1,1,2,3]
t = [2,3,1,1]
in_channel = 3
out_channel = 5
ein = 3
g = GNNGraph(s, t)
x = randn(Float32, 3, g.num_nodes)

# create layer
l = GATv2Conv((in_channel, ein) => out_channel, add_self_loops = false)

# edge features
e = randn(Float32, ein, length(s))

# forward pass
y = l(g, x, e)    
```
