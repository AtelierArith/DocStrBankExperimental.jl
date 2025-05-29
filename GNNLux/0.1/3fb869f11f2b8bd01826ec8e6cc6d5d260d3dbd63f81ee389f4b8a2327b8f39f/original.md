```
GConvLSTM(in => out, k; use_bias = true, init_weight = glorot_uniform, init_state = zeros32, init_bias = zeros32)
```

Graph Convolutional Long Short-Term Memory (GConvLSTM) recurrent layer from the paper [Structured Sequence Modeling with Graph Convolutional Recurrent Networks](https://arxiv.org/pdf/1612.07659). 

Performs a layer of ChebConv to model spatial dependencies, followed by a Long Short-Term Memory (LSTM) cell to model temporal dependencies.

# Arguments

  * `in`: Number of input features.
  * `out`: Number of output features.
  * `k`: Chebyshev polynomial order.
  * `use_bias`: Add learnable bias. Default `true`.
  * `init_weight`: Weights' initializer. Default `glorot_uniform`.
  * `init_state`: Initial state of the hidden stat of the GRU layer. Default `zeros32`.
  * `init_bias`: Bias initializer. Default `zeros32`.

# Examples

```julia
using GNNLux, Lux, Random

# initialize random number generator
rng = Random.default_rng()

# create data
g = rand_graph(rng, 5, 10)
x = rand(rng, Float32, 2, 5)

# create GConvLSTM layer
l = GConvLSTM(2 => 5, 2)

# setup layer
ps, st = LuxCore.setup(rng, l)

# forward pass
y, st = l(g, x, ps, st)      # result size (5, 5)
```
