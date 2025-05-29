```
GConvLSTM(args...; kws...)
```

Construct a recurrent layer corresponding to the [`GConvLSTMCell`](@ref) cell. It can be used to process an entire temporal sequence of node features at once.

The arguments are passed to the [`GConvLSTMCell`](@ref) constructor. See [`GNNRecurrence`](@ref) for more details.

# Examples

```jldoctest
julia> num_nodes, num_edges = 5, 10;

julia> d_in, d_out = 2, 3;

julia> timesteps = 5;

julia> g = rand_graph(num_nodes, num_edges);

julia> x = rand(Float32, d_in, timesteps, num_nodes);

julia> layer = GConvLSTM(d_in => d_out, 2)
GNNRecurrence(
  GConvLSTMCell(2 => 3, 2),             # 168 parameters
)                   # Total: 24 arrays, 168 parameters, 2.023 KiB.

julia> y = layer(g, x);

julia> size(y) # (d_out, timesteps, num_nodes)
(3, 5, 5)
```
