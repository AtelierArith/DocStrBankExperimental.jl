```
DCGRU(args...; kws...)
```

Construct a recurrent layer corresponding to the [`DCGRUCell`](@ref) cell. It can be used to process an entire temporal sequence of node features at once.

The arguments are passed to the [`DCGRUCell`](@ref) constructor. See [`GNNRecurrence`](@ref) for more details.

# Examples

```jldoctest
julia> num_nodes, num_edges = 5, 10;

julia> d_in, d_out = 2, 3;

julia> timesteps = 5;

julia> g = rand_graph(num_nodes, num_edges);

julia> x = rand(Float32, d_in, timesteps, num_nodes);

julia> layer = DCGRU(d_in => d_out, 2)
GNNRecurrence(
  DCGRUCell(2 => 3, 2),                 # 189 parameters
)                   # Total: 6 arrays, 189 parameters, 1.184 KiB.

julia> y = layer(g, x);

julia> size(y) # (d_out, timesteps, num_nodes)
(3, 5, 5)
```
