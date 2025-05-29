```
CGConv((in, ein) => out, act=identity; bias=true, init=glorot_uniform, residual=false)
CGConv(in => out, ...)
```

The crystal graph convolutional layer from the paper [Crystal Graph Convolutional Neural Networks for an Accurate and Interpretable Prediction of Material Properties](https://arxiv.org/pdf/1710.10324.pdf). Performs the operation

$$
\mathbf{x}_i' = \mathbf{x}_i + \sum_{j\in N(i)}\sigma(W_f \mathbf{z}_{ij} + \mathbf{b}_f)\, act(W_s \mathbf{z}_{ij} + \mathbf{b}_s)
$$

where $\mathbf{z}_{ij}$  is the node and edge features concatenation  $[\mathbf{x}_i; \mathbf{x}_j; \mathbf{e}_{j\to i}]$  and $\sigma$ is the sigmoid function. The residual $\mathbf{x}_i$ is added only if `residual=true` and the output size is the same  as the input size.

# Arguments

  * `in`: The dimension of input node features.
  * `ein`: The dimension of input edge features.

If `ein` is not given, assumes that no edge features are passed as input in the forward pass.

  * `out`: The dimension of output node features.
  * `act`: Activation function.
  * `bias`: Add learnable bias.
  * `init`: Weights' initializer.
  * `residual`: Add a residual connection.

# Examples

```julia
g = rand_graph(5, 6)
x = rand(Float32, 2, g.num_nodes)
e = rand(Float32, 3, g.num_edges)

l = CGConv((2, 3) => 4, tanh)
y = l(g, x, e)    # size: (4, num_nodes)

# No edge features
l = CGConv(2 => 4, tanh)
y = l(g, x)    # size: (4, num_nodes)
```
