```
TGCN(args...; kws...)
```

Construct a recurrent layer corresponding to the [`TGCNCell`](@ref) cell.

The arguments are passed to the [`TGCNCell`](@ref) constructor. See [`GNNRecurrence`](@ref) for more details.

# Examples

```jldoctest
julia> num_nodes, num_edges = 5, 10;

julia> d_in, d_out = 2, 3;

julia> timesteps = 5;

julia> g = rand_graph(num_nodes, num_edges);

julia> x = rand(Float32, d_in, timesteps, num_nodes);

julia> layer = TGCN(d_in => d_out)

julia> y = layer(g, x);

julia> size(y) # (d_out, timesteps, num_nodes)
(3, 5, 5)
```
