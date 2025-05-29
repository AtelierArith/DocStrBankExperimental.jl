```
rand_graph([rng,] n, m; bidirected=true, edge_weight = nothing, kws...)
```

Generate a random (Erdós-Renyi) `GNNGraph` with `n` nodes and `m` edges.

If `bidirected=true` the reverse edge of each edge will be present. If `bidirected=false` instead, `m` unrelated edges are generated. In any case, the output graph will contain no self-loops or multi-edges.

A vector can be passed  as `edge_weight`. Its length has to be equal to `m` in the directed case, and `m÷2` in the bidirected one.

Pass a random number generator as the first argument to make the generation reproducible.

Additional keyword arguments will be passed to the [`GNNGraph`](@ref) constructor.

# Examples

```julia
julia> g = rand_graph(5, 4, bidirected=false)
GNNGraph:
  num_nodes: 5
  num_edges: 4

julia> edge_index(g)
([4, 3, 2, 1], [5, 4, 3, 2])

# In the bidirected case, edge data will be duplicated on the reverse edges if needed.
julia> g = rand_graph(5, 4, edata=rand(Float32, 16, 2))
GNNGraph:
  num_nodes: 5
  num_edges: 4
  edata:
        e = 16×4 Matrix{Float32}

# Each edge has a reverse
julia> edge_index(g)
([1, 1, 5, 3], [5, 3, 1, 1])
```
