```
SGConv(int => out, k=1; [bias, init, add_self_loops, use_edge_weight])
```

SGC layer from [Simplifying Graph Convolutional Networks](https://arxiv.org/pdf/1902.07153.pdf) Performs operation

$$
H^{K} = (\tilde{D}^{-1/2} \tilde{A} \tilde{D}^{-1/2})^K X \Theta
$$

where $\tilde{A}$ is $A + I$.

# Arguments

  * `in`: Number of input features.
  * `out`: Number of output features.
  * `k` : Number of hops k. Default `1`.
  * `bias`: Add learnable bias. Default `true`.
  * `init`: Weights' initializer. Default `glorot_uniform`.
  * `add_self_loops`: Add self loops to the graph before performing the convolution. Default `false`.
  * `use_edge_weight`: If `true`, consider the edge weights in the input graph (if available).                    If `add_self_loops=true` the new weights will be set to 1. Default `false`.

# Examples

```julia
# create data
s = [1,1,2,3]
t = [2,3,1,1]
g = GNNGraph(s, t)
x = randn(Float32, 3, g.num_nodes)

# create layer
l = SGConv(3 => 5; add_self_loops = true) 

# forward pass
y = l(g, x)       # size:  5 × num_nodes

# convolution with edge weights
w = [1.1, 0.1, 2.3, 0.5]
y = l(g, x, w)

# Edge weights can also be embedded in the graph.
g = GNNGraph(s, t, w)
l = SGConv(3 => 5, add_self_loops = true, use_edge_weight=true) 
y = l(g, x) # same as l(g, x, w) 
```
