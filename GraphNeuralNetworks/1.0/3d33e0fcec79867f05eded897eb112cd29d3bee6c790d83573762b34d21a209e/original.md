```
ResGatedGraphConv(in => out, act=identity; init=glorot_uniform, bias=true)
```

The residual gated graph convolutional operator from the [Residual Gated Graph ConvNets](https://arxiv.org/abs/1711.07553) paper.

The layer's forward pass is given by

$$
\mathbf{x}_i' = act\big(U\mathbf{x}_i + \sum_{j \in N(i)} \eta_{ij} V \mathbf{x}_j\big),
$$

where the edge gates $\eta_{ij}$ are given by

$$
\eta_{ij} = sigmoid(A\mathbf{x}_i + B\mathbf{x}_j).
$$

# Arguments

  * `in`: The dimension of input features.
  * `out`: The dimension of output features.
  * `act`: Activation function.
  * `init`: Weight matrices' initializing function.
  * `bias`: Learn an additive bias if true.

# Examples:

```julia
# create data
s = [1,1,2,3]
t = [2,3,1,1]
in_channel = 3
out_channel = 5
g = GNNGraph(s, t)

# create layer
l = ResGatedGraphConv(in_channel => out_channel, tanh, bias = true)

# forward pass
y = l(g, x)  
```
