```
GNNChain(layers...)
GNNChain(name = layer, ...)
```

Collects multiple layers / functions to be called in sequence on given input graph and input node features. 

It allows to compose layers in a sequential fashion as `Flux.Chain` does, propagating the output of each layer to the next one. In addition, `GNNChain` handles the input graph as well, providing it  as a first argument only to layers subtyping the [`GNNLayer`](@ref) abstract type. 

`GNNChain` supports indexing and slicing, `m[2]` or `m[1:end-1]`, and if names are given, `m[:name] == m[1]` etc.

# Examples

```jldoctest
julia> using Flux, GraphNeuralNetworks

julia> m = GNNChain(GCNConv(2=>5), 
                    BatchNorm(5), 
                    x -> relu.(x), 
                    Dense(5, 4))
GNNChain(GCNConv(2 => 5), BatchNorm(5), #7, Dense(5 => 4))

julia> x = randn(Float32, 2, 3);

julia> g = rand_graph(3, 6)
GNNGraph:
    num_nodes = 3
    num_edges = 6

julia> m(g, x)
4×3 Matrix{Float32}:
    -0.795592  -0.795592  -0.795592
    -0.736409  -0.736409  -0.736409
    0.994925   0.994925   0.994925
    0.857549   0.857549   0.857549

julia> m2 = GNNChain(enc = m, 
                     dec = DotDecoder())
GNNChain(enc = GNNChain(GCNConv(2 => 5), BatchNorm(5), #7, Dense(5 => 4)), dec = DotDecoder())

julia> m2(g, x)
1×6 Matrix{Float32}:
 2.90053  2.90053  2.90053  2.90053  2.90053  2.90053

julia> m2[:enc](g, x) == m(g, x)
true
```
