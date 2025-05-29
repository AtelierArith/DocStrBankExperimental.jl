```
EvolveGCNO(ch; use_bias = true, init_weight = glorot_uniform, init_state = zeros32, init_bias = zeros32)
```

Evolving Graph Convolutional Network (EvolveGCNO) layer from the paper [EvolveGCN: Evolving Graph Convolutional Networks for Dynamic Graphs](https://arxiv.org/pdf/1902.10191).

Perfoms a Graph Convolutional layer with parameters derived from a Long Short-Term Memory (LSTM) layer across the snapshots of the temporal graph.

# Arguments

  * `in`: Number of input features.
  * `out`: Number of output features.
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
tg = TemporalSnapshotsGNNGraph([rand_graph(rng, 10, 20; ndata = rand(rng, 4, 10)), rand_graph(rng, 10, 14; ndata = rand(rng, 4, 10)), rand_graph(rng, 10, 22; ndata = rand(rng, 4, 10))])

# create layer
l = EvolveGCNO(4 => 5)

# setup layer
ps, st = LuxCore.setup(rng, l)

# forward pass
y, st = l(tg, tg.ndata.x , ps, st)      # result size 3, size y[1] (5, 10)
```
