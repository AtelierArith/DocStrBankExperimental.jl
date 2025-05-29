```
TransformerConv((in, ein) => out; [heads, concat, init, add_self_loops, bias_qkv,
    bias_root, root_weight, gating, skip_connection, batch_norm, ff_channels]))
```

The transformer-like multi head attention convolutional operator from the  [Masked Label Prediction: Unified Message Passing Model for Semi-Supervised  Classification](https://arxiv.org/abs/2009.03509) paper, which also considers  edge features. It further contains options to also be configured as the transformer-like convolutional operator from the  [Attention, Learn to Solve Routing Problems!](https://arxiv.org/abs/1706.03762) paper, including a successive feed-forward network as well as skip layers and batch normalization.

The layer's basic forward pass is given by

$$
x_i' = W_1x_i + \sum_{j\in N(i)} \alpha_{ij} (W_2 x_j + W_6e_{ij})
$$

where the attention scores are

$$
\alpha_{ij} = \mathrm{softmax}\left(\frac{(W_3x_i)^T(W_4x_j+
W_6e_{ij})}{\sqrt{d}}\right).
$$

Optionally, a combination of the aggregated value with transformed root node features  by a gating mechanism via

$$
x'_i = \beta_i W_1 x_i + (1 - \beta_i) \underbrace{\left(\sum_{j \in \mathcal{N}(i)}
\alpha_{i,j} W_2 x_j \right)}_{=m_i}
$$

with

$$
\beta_i = \textrm{sigmoid}(W_5^{\top} [ W_1 x_i, m_i, W_1 x_i - m_i ]).
$$

can be performed.

# Arguments

  * `in`: Dimension of input features, which also corresponds to the dimension of    the output features.
  * `ein`: Dimension of the edge features; if 0, no edge features will be used.
  * `out`: Dimension of the output.
  * `heads`: Number of heads in output. Default `1`.
  * `concat`: Concatenate layer output or not. If not, layer output is averaged   over the heads. Default `true`.
  * `init`: Weight matrices' initializing function. Default `glorot_uniform`.
  * `add_self_loops`: Add self loops to the input graph. Default `false`.
  * `bias_qkv`: If set, bias is used in the key, query and value transformations for nodes.   Default `true`.
  * `bias_root`: If set, the layer will also learn an additive bias for the root when root    weight is used. Default `true`.
  * `root_weight`: If set, the layer will add the transformed root node features   to the output. Default `true`.
  * `gating`: If set, will combine aggregation and transformed root node features by a   gating mechanism. Default `false`.
  * `skip_connection`: If set, a skip connection will be made from the input and    added to the output. Default `false`.
  * `batch_norm`: If set, a batch normalization will be applied to the output. Default `false`.
  * `ff_channels`: If positive, a feed-forward NN is appended, with the first having the given   number of hidden nodes; this NN also gets a skip connection and batch normalization    if the respective parameters are set. Default: `0`.

# Examples

```julia
N, in_channel, out_channel = 4, 3, 5
ein, heads = 2, 3
g = GNNGraph([1,1,2,4], [2,3,1,1])
l = TransformerConv((in_channel, ein) => in_channel; heads, gating = true, bias_qkv = true)
x = rand(Float32, in_channel, N)
e = rand(Float32, ein, g.num_edges)
l(g, x, e)
```
