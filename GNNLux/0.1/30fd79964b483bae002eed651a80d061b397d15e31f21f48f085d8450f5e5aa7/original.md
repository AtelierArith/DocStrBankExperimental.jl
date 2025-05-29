```
MEGNetConv(ϕe, ϕv; aggr=mean)
MEGNetConv(in => out; aggr=mean)
```

Convolution from [Graph Networks as a Universal Machine Learning Framework for Molecules and Crystals](https://arxiv.org/pdf/1812.05055.pdf) paper. In the forward pass, takes as inputs node features `x` and edge features `e` and returns updated features `x'` and `e'` according to 

$$
\begin{aligned}
\mathbf{e}_{i\to j}'  = \phi_e([\mathbf{x}_i;\,  \mathbf{x}_j;\,  \mathbf{e}_{i\to j}]),\\
\mathbf{x}_{i}'  = \phi_v([\mathbf{x}_i;\, \square_{j\in \mathcal{N}(i)}\,\mathbf{e}_{j\to i}']).
\end{aligned}
$$

`aggr` defines the aggregation to be performed.

If the neural networks `ϕe` and  `ϕv` are not provided, they will be constructed from the `in` and `out` arguments instead as multi-layer perceptron with one hidden layer and `relu`  activations.

# Examples

```julia
using GNNLux, Lux, Random

# initialize random number generator
rng = Random.default_rng()

# create a random graph
g = rand_graph(rng, 10, 30)
x = randn(rng, Float32, 3, 10)
e = randn(rng, Float32, 3, 30)

# create a MEGNetConv layer
m = MEGNetConv(3 => 3)

# setup layer
ps, st = LuxCore.setup(rng, m)

# forward pass
(x′, e′), st = m(g, x, e, ps, st)
```
