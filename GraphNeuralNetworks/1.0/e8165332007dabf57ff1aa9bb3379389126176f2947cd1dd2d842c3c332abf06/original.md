```
DCGRUCell(in => out, k; [bias, init])
```

Diffusion Convolutional Recurrent Neural Network (DCGRU) cell from the paper  [Diffusion Convolutional Recurrent Neural Network: Data-driven Traffic Forecasting](https://arxiv.org/abs/1707.01926).

Applyis a [`DConv`](@ref) layer to model spatial dependencies,  in combination with a Gated Recurrent Unit (GRU) cell to model temporal dependencies.

# Arguments

  * `in`: Number of input node features.
  * `out`: Number of output node features.
  * `k`: Diffusion step for the `DConv`.
  * `bias`: Add learnable bias. Default `true`.
  * `init`: Convolution weights' initializer. Default `glorot_uniform`.

# Forward

```
cell(g::GNNGraph, x, [h])
```

  * `g`: The input graph.
  * `x`: The node features. It should be a matrix of size `in x num_nodes`.
  * `h`: The current state of the GRU cell. It is a matrix of size `out x num_nodes`.      If not provided, it is assumed to be a matrix of zeros.

Performs one recurrence step and returns a tuple `(h, h)`, where `h` is the updated hidden state of the GRU cell.

# Examples

```jldoctest
julia> using GraphNeuralNetworks, Flux

julia> num_nodes, num_edges = 5, 10;

julia> d_in, d_out = 2, 3;

julia> timesteps = 5;

julia> g = rand_graph(num_nodes, num_edges);

julia> x = [rand(Float32, d_in, num_nodes) for t in 1:timesteps];

julia> cell = DCGRUCell(d_in => d_out, 2);

julia> state = Flux.initialstates(cell);

julia> y = state;

julia> for xt in x
           y, state = cell(g, xt, state)
       end

julia> size(y) # (d_out, num_nodes)
(3, 5)
```
