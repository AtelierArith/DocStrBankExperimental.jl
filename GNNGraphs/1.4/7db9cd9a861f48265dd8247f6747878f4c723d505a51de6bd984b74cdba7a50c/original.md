```
rand_bipartite_heterograph([rng,] 
                           (n1, n2), (m12, m21); 
                           bidirected = true, 
                           node_t = (:A, :B), 
                           edge_t = :to, 
                           kws...)
```

Construct an [`GNNHeteroGraph`](@ref) with random edges representing a bipartite graph. The graph will have two types of nodes, and edges will only connect nodes of different types.

The first argument is a tuple `(n1, n2)` specifying the number of nodes of each type. The second argument is a tuple `(m12, m21)` specifying the number of edges connecting nodes of type `1` to nodes of type `2`  and vice versa.

The type of nodes and edges can be specified with the `node_t` and `edge_t` keyword arguments, which default to `(:A, :B)` and `:to` respectively.

If `bidirected=true` (default), the reverse edge of each edge will be present. In this case `m12 == m21` is required.

A random number generator can be passed as the first argument to make the generation reproducible.

Additional keyword arguments will be passed to the [`GNNHeteroGraph`](@ref) constructor.

See [`rand_heterograph`](@ref) for a more general version.

# Examples

```julia
julia> g = rand_bipartite_heterograph((10, 15), 20)
GNNHeteroGraph:
  num_nodes: (:A => 10, :B => 15)
  num_edges: ((:A, :to, :B) => 20, (:B, :to, :A) => 20)

julia> g = rand_bipartite_heterograph((10, 15), (20, 0), node_t=(:user, :item), edge_t=:-, bidirected=false)
GNNHeteroGraph:
  num_nodes: Dict(:item => 15, :user => 10)
  num_edges: Dict((:item, :-, :user) => 0, (:user, :-, :item) => 20)
```
