```
GINConv(f, ϵ; aggr=+)
```

Graph Isomorphism convolutional layer from paper [How Powerful are Graph Neural Networks?](https://arxiv.org/pdf/1810.00826.pdf).

Implements the graph convolution

$$
\mathbf{x}_i' = f_\Theta\left((1 + \epsilon) \mathbf{x}_i + \sum_{j \in N(i)} \mathbf{x}_j \right)
$$

where $f_\Theta$ typically denotes a learnable function, e.g. a linear layer or a multi-layer perceptron.

# Arguments

  * `f`: A (possibly learnable) function acting on node features.
  * `ϵ`: Weighting factor.

# Examples:

```julia
# create data
s = [1,1,2,3]
t = [2,3,1,1]
in_channel = 3
out_channel = 5
g = GNNGraph(s, t)

# create dense layer
nn = Dense(in_channel, out_channel)

# create layer
l = GINConv(nn, 0.01f0, aggr = mean)

# forward pass
y = l(g, x)  
```
