```
GNNChain(layers...)
GNNChain(name = layer, ...)
```

Collects multiple layers / functions to be called in sequence on given input graph and input node features. 

It allows to compose layers in a sequential fashion as `Lux.Chain` does, propagating the output of each layer to the next one. In addition, `GNNChain` handles the input graph as well, providing it  as a first argument only to layers subtyping the [`GNNLayer`](@ref) abstract type. 

`GNNChain` supports indexing and slicing, `m[2]` or `m[1:end-1]`, and if names are given, `m[:name] == m[1]` etc.

# Examples

```jldoctest
julia> using Lux, GNNLux, Random

julia> rng = Random.default_rng();

julia> m = GNNChain(GCNConv(2=>5), 
                    x -> relu.(x), 
                    Dense(5=>4))

julia> x = randn(rng, Float32, 2, 3);

julia> g = rand_graph(rng, 3, 6)
GNNGraph:
  num_nodes: 3
  num_edges: 6

julia> ps, st = LuxCore.setup(rng, m);

julia> m(g, x, ps, st)     # First entry is the output, second entry is the state of the model
(Float32[-0.15594329 -0.15594329 -0.15594329; 0.93431795 0.93431795 0.93431795; 0.27568763 0.27568763 0.27568763; 0.12568939 0.12568939 0.12568939], (layer_1 = NamedTuple(), layer_2 = NamedTuple(), layer_3 = NamedTuple()))
```
