```
DotDecoder()
```

A graph neural network layer that  for given input graph `g` and node features `x`, returns the dot product `x_i ⋅ xj` on each edge. 

# Examples

```jldoctest
julia> g = rand_graph(5, 6)
GNNGraph:
    num_nodes = 5
    num_edges = 6

julia> dotdec = DotDecoder()
DotDecoder()

julia> dotdec(g, rand(2, 5))
1×6 Matrix{Float64}:
 0.345098  0.458305  0.106353  0.345098  0.458305  0.106353
```
