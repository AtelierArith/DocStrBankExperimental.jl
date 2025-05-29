```
A3TGCN(in => out; use_bias = true, init_weight = glorot_uniform, init_state = zeros32, init_bias = zeros32, add_self_loops = false, use_edge_weight = true)
```

Attention Temporal Graph Convolutional Network (A3T-GCN) model from the paper [A3T-GCN: Attention Temporal Graph Convolutional Network for Traffic Forecasting](https://arxiv.org/pdf/2006.11583.pdf).

Performs a TGCN layer, followed by a soft attention layer.

# Arguments

  * `in`: Number of input features.
  * `out`: Number of output features.
  * `use_bias`: Add learnable bias. Default `true`.
  * `init_weight`: Weights' initializer. Default `glorot_uniform`.
  * `init_state`: Initial state of the hidden stat of the GRU layer. Default `zeros32`.
  * `init_bias`: Bias initializer. Default `zeros32`.
  * `add_self_loops`: Add self loops to the graph before performing the convolution. Default `false`.
  * `use_edge_weight`: If `true`, consider the edge weights in the input graph (if available).                    If `add_self_loops=true` the new weights will be set to 1.                     This option is ignored if the `edge_weight` is explicitly provided in the forward pass.                    Default `false`.

# Examples

```julia
using GNNLux, Lux, Random

# initialize random number generator
rng = Random.default_rng()

# create data
g = rand_graph(rng, 5, 10)
x = rand(rng, Float32, 2, 5)

# create A3TGCN layer
l = A3TGCN(2 => 6)

# setup layer
ps, st = LuxCore.setup(rng, l)

# forward pass
y, st = l(g, x, ps, st)      # result size (6, 5)
```
