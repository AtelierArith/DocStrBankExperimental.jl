```
GCNConv(in => out, σ=identity; [bias, init, add_self_loops, use_edge_weight])
```

Graph convolutional layer from paper [Semi-supervised Classification with Graph Convolutional Networks](https://arxiv.org/abs/1609.02907).

Performs the operation

$$
\mathbf{x}'_i = \sum_{j\in N(i)} a_{ij} W \mathbf{x}_j
$$

where $a_{ij} = 1 / \sqrt{|N(i)||N(j)|}$ is a normalization factor computed from the node degrees. 

If the input graph has weighted edges and `use_edge_weight=true`, than $a_{ij}$ will be computed as

$$
a_{ij} = \frac{e_{j\to i}}{\sqrt{\sum_{j \in N(i)}  e_{j\to i}} \sqrt{\sum_{i \in N(j)}  e_{i\to j}}}
$$

The input to the layer is a node feature array `X` of size `(num_features, num_nodes)` and optionally an edge weight vector.

# Arguments

  * `in`: Number of input features.
  * `out`: Number of output features.
  * `σ`: Activation function. Default `identity`.
  * `bias`: Add learnable bias. Default `true`.
  * `init`: Weights' initializer. Default `glorot_uniform`.
  * `add_self_loops`: Add self loops to the graph before performing the convolution. Default `false`.
  * `use_edge_weight`: If `true`, consider the edge weights in the input graph (if available).                    If `add_self_loops=true` the new weights will be set to 1.                     This option is ignored if the `edge_weight` is explicitly provided in the forward pass.                    Default `false`.

# Forward

```
(::GCNConv)(g::GNNGraph, x, edge_weight = nothing; norm_fn = d -> 1 ./ sqrt.(d), conv_weight = nothing) -> AbstractMatrix
```

Takes as input a graph `g`, a node feature matrix `x` of size `[in, num_nodes]`, and optionally an edge weight vector. Returns a node feature matrix of size  `[out, num_nodes]`.

The `norm_fn` parameter allows for custom normalization of the graph convolution operation by passing a function as argument.  By default, it computes $\frac{1}{\sqrt{d}}$ i.e the inverse square root of the degree (`d`) of each node in the graph.  If `conv_weight` is an `AbstractMatrix` of size `[out, in]`, then the convolution is performed using that weight matrix instead of the weights stored in the model.

# Examples

```julia
# create data
s = [1,1,2,3]
t = [2,3,1,1]
g = GNNGraph(s, t)
x = randn(Float32, 3, g.num_nodes)

# create layer
l = GCNConv(3 => 5) 

# forward pass
y = l(g, x)       # size:  5 × num_nodes

# convolution with edge weights and custom normalization function
w = [1.1, 0.1, 2.3, 0.5]
custom_norm_fn(d) = 1 ./ sqrt.(d + 1)  # Custom normalization function
y = l(g, x, w; norm_fn = custom_norm_fn)

# Edge weights can also be embedded in the graph.
g = GNNGraph(s, t, w)
l = GCNConv(3 => 5, use_edge_weight=true) 
y = l(g, x) # same as l(g, x, w) 
```
