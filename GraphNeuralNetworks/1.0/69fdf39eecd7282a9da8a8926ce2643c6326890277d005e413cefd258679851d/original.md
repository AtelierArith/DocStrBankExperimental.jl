```
GMMConv((in, ein) => out, σ=identity; K=1, bias=true, init=glorot_uniform, residual=false)
```

Graph mixture model convolution layer from the paper [Geometric deep learning on graphs and manifolds using mixture model CNNs](https://arxiv.org/abs/1611.08402) Performs the operation

$$
\mathbf{x}_i' = \mathbf{x}_i + \frac{1}{|N(i)|} \sum_{j\in N(i)}\frac{1}{K}\sum_{k=1}^K \mathbf{w}_k(\mathbf{e}_{j\to i}) \odot \Theta_k \mathbf{x}_j
$$

where $w^a_{k}(e^a)$ for feature `a` and kernel `k` is given by

$$
w^a_{k}(e^a) = \exp(-\frac{1}{2}(e^a - \mu^a_k)^T (\Sigma^{-1})^a_k(e^a - \mu^a_k))
$$

$\Theta_k, \mu^a_k, (\Sigma^{-1})^a_k$ are learnable parameters.

The input to the layer is a node feature array `x` of size `(num_features, num_nodes)` and edge pseudo-coordinate array `e` of size `(num_features, num_edges)` The residual $\mathbf{x}_i$ is added only if `residual=true` and the output size is the same  as the input size.

# Arguments

  * `in`: Number of input node features.
  * `ein`: Number of input edge features.
  * `out`: Number of output features.
  * `σ`: Activation function. Default `identity`.
  * `K`: Number of kernels. Default `1`.
  * `bias`: Add learnable bias. Default `true`.
  * `init`: Weights' initializer. Default `glorot_uniform`.
  * `residual`: Residual conncetion. Default `false`.

# Examples

```julia
# create data
s = [1,1,2,3]
t = [2,3,1,1]
g = GNNGraph(s,t)
nin, ein, out, K = 4, 10, 7, 8 
x = randn(Float32, nin, g.num_nodes)
e = randn(Float32, ein, g.num_edges)

# create layer
l = GMMConv((nin, ein) => out, K=K)

# forward pass
l(g, x, e)
```
