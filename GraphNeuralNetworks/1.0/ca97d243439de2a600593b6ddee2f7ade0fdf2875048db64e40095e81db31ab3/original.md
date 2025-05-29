```
ChebConv(in => out, k; bias=true, init=glorot_uniform)
```

Chebyshev spectral graph convolutional layer from paper [Convolutional Neural Networks on Graphs with Fast Localized Spectral Filtering](https://arxiv.org/abs/1606.09375).

Implements

$$
X' = \sum^{K-1}_{k=0}  W^{(k)} Z^{(k)}
$$

where $Z^{(k)}$ is the $k$-th term of Chebyshev polynomials, and can be calculated by the following recursive form:

$$
\begin{aligned}
Z^{(0)} &= X \\
Z^{(1)} &= \hat{L} X \\
Z^{(k)} &= 2 \hat{L} Z^{(k-1)} - Z^{(k-2)}
\end{aligned}
$$

with $\hat{L}$ the [`scaled_laplacian`](@ref).

# Arguments

  * `in`: The dimension of input features.
  * `out`: The dimension of output features.
  * `k`: The order of Chebyshev polynomial.
  * `bias`: Add learnable bias.
  * `init`: Weights' initializer.

# Examples

```julia
# create data
s = [1,1,2,3]
t = [2,3,1,1]
g = GNNGraph(s, t)
x = randn(Float32, 3, g.num_nodes)

# create layer
l = ChebConv(3 => 5, 5) 

# forward pass
y = l(g, x)       # size:  5 × num_nodes
```
