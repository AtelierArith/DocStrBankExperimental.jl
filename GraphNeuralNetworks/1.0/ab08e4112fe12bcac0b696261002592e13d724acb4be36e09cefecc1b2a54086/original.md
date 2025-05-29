```
GConvLSTMCell(in => out, k; [bias, init])
```

Graph Convolutional LSTM recurrent cell from the paper  [Structured Sequence Modeling with Graph Convolutional Recurrent Networks](https://arxiv.org/abs/1612.07659).

Uses [`ChebConv`](@ref) to model spatial dependencies,  followed by a Long Short-Term Memory (LSTM) cell to model temporal dependencies.

# Arguments

  * `in => out`: A pair  where `in` is the number of input node features and `out`  is the number of output node features.
  * `k`: Chebyshev polynomial order.
  * `bias`: Add learnable bias. Default `true`.
  * `init`: Weights' initializer. Default `glorot_uniform`.

# Forward

```
cell(g::GNNGraph, x, [state])
```

  * `g`: The input graph.
  * `x`: The node features. It should be a matrix of size `in x num_nodes`.
  * `state`: The current state of the LSTM cell.        If given, it is a tuple `(h, c)` where both `h` and `c` are arrays of size `out x num_nodes`.      If not provided, it is assumed to be a tuple of matrices of zeros.

Performs one recurrence step and returns a tuple `(output, state)`,  where `output` is the updated hidden state `h` of the LSTM cell and `state` is the updated tuple `(h, c)`.

# Examples

```jldoctest
julia> using GraphNeuralNetworks, Flux

julia> num_nodes, num_edges = 5, 10;

julia> d_in, d_out = 2, 3;

julia> timesteps = 5;

julia> g = rand_graph(num_nodes, num_edges);

julia> x = [rand(Float32, d_in, num_nodes) for t in 1:timesteps];

julia> cell = GConvLSTMCell(d_in => d_out, 2);

julia> state = Flux.initialstates(cell);

julia> y = state[1];

julia> for xt in x
           y, state = cell(g, xt, state)
       end

julia> size(y) # (d_out, num_nodes)
(3, 5)
```
