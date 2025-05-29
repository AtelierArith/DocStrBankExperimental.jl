```
EGNNConv((in, ein) => out; hidden_size=2in, residual=false)
EGNNConv(in => out; hidden_size=2in, residual=false)
```

Equivariant Graph Convolutional Layer from [E(n) Equivariant Graph Neural Networks](https://arxiv.org/abs/2102.09844).

The layer performs the following operation:

$$
\begin{aligned}
\mathbf{m}_{j\to i} &=\phi_e(\mathbf{h}_i, \mathbf{h}_j, \lVert\mathbf{x}_i-\mathbf{x}_j\rVert^2, \mathbf{e}_{j\to i}),\\
\mathbf{x}_i' &= \mathbf{x}_i + C_i\sum_{j\in\mathcal{N}(i)}(\mathbf{x}_i-\mathbf{x}_j)\phi_x(\mathbf{m}_{j\to i}),\\
\mathbf{m}_i &= C_i\sum_{j\in\mathcal{N}(i)} \mathbf{m}_{j\to i},\\
\mathbf{h}_i' &= \mathbf{h}_i + \phi_h(\mathbf{h}_i, \mathbf{m}_i)
\end{aligned}
$$

where $\mathbf{h}_i$, $\mathbf{x}_i$, $\mathbf{e}_{j\to i}$ are invariant node features, equivariant node features, and edge features respectively. $\phi_e$, $\phi_h$, and $\phi_x$ are two-layer MLPs. `C` is a constant for normalization, computed as $1/|\mathcal{N}(i)|$.

# Constructor Arguments

  * `in`: Number of input features for `h`.
  * `out`: Number of output features for `h`.
  * `ein`: Number of input edge features.
  * `hidden_size`: Hidden representation size.
  * `residual`: If `true`, add a residual connection. Only possible if `in == out`. Default `false`.

# Forward Pass

```
l(g, x, h, e=nothing, ps, st)
```

## Forward Pass Arguments:

  * `g` : The graph.
  * `x` : Matrix of equivariant node coordinates.
  * `h` : Matrix of invariant node features.
  * `e` : Matrix of invariant edge features. Default `nothing`.
  * `ps` : Parameters.
  * `st` : State.

Returns updated `h` and `x`.

# Examples

```julia
using GNNLux, Lux, Random

# initialize random number generator
rng = Random.default_rng()

# create random graph
g = rand_graph(rng, 10, 10)
h = randn(rng, Float32, 5, g.num_nodes)
x = randn(rng, Float32, 3, g.num_nodes)

egnn = EGNNConv(5 => 6, 10)

# setup layer
ps, st = LuxCore.setup(rng, egnn)

# forward pass
(hnew, xnew), st = egnn(g, h, x, ps, st)
```
