```
edge_indices(g::FactorGraph, v::FactorGraphVertex)
```

Return a lazy iterator to the indices of the edges incident on vertex `v`, with `v`.

The output of `edge_indices` does not allocate and it can be used to index external arrays of properties directly

# Examples

```jldoctest edge_indices
julia> using IndexedFactorGraphs, Test

julia> g = FactorGraph([0 1 1 0;
                        1 0 0 0;
                        0 0 1 1])
FactorGraph{Int64} with 4 variables, 3 factors, and 5 edges

julia> edgeprops = randn(ne(g));

julia> indices = (idx(e) for e in outedges(g, variable(3)));

julia> indices_noalloc = edge_indices(g, variable(3));

julia> @assert edgeprops[collect(indices)] == edgeprops[indices_noalloc]

julia> @test_throws ArgumentError edgeprops[indices]
Test Passed
      Thrown: ArgumentError
```
