```
rand_heterograph([rng,] n, m; bidirected=false, kws...)
```

Construct an [`GNNHeteroGraph`](@ref) with random edges and with number of nodes and edges  specified by `n` and `m` respectively. `n` and `m` can be any iterable of pairs specifing node/edge types and their numbers.

Pass a random number generator as a first argument to make the generation reproducible.

Setting `bidirected=true` will generate a bidirected graph, i.e. each edge will have a reverse edge. Therefore, for each edge type `(:A, :rel, :B)` a corresponding reverse edge type `(:B, :rel, :A)` will be generated.

Additional keyword arguments will be passed to the [`GNNHeteroGraph`](@ref) constructor.

# Examples

```jldoctest
julia> g = rand_heterograph((:user => 10, :movie => 20),
                            (:user, :rate, :movie) => 30)
GNNHeteroGraph:
  num_nodes: Dict(:movie => 20, :user => 10)
  num_edges: Dict((:user, :rate, :movie) => 30)
```
