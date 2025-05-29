```
BiCM(G::T; precision::N=Float64, kwargs...) where {T<:Graphs.AbstractGraph, N<:Real}
BiCM(;d⊥::Vector{T}, d⊤::Vector{T}, precision::Type{<:AbstractFloat}=Float64, kwargs...)
```

Constructor function for the `BiCM` type. The graph you provide should be bipartite

By default and dependng on the graph type `T`, the definition of degree from $Graphs.jl$ is applied.  If you want to use a different definition of degrees, you can pass vectors of degrees sequences as keyword arguments (`d⊥`, `d⊤`). If you want to generate a model directly from degree sequences without an underlying graph , you can simply pass the degree sequences as arguments (`d⊥`, `d⊤`). If you want to work from an adjacency matrix, or edge list, you can use the graph constructors from the $JuliaGraphs$ ecosystem.

Zero degree nodes have a zero probability of being connected to other nodes, so they are skipped in the computation of the model.

# Examples

```jldoctest
# generating a model from a graph
julia> G = corporateclub();

julia> model =  BiCM(G)
BiCM{Graphs.SimpleGraphs.SimpleGraph{Int64}, Float64} (25 + 15 vertices, 6 + 6 unique degrees, 0.30 compression ratio)

```

```jldoctest
# generating a model directly from a degree sequence
julia> model = model = BiCM(d⊥=[1,1,2,2,2,3,3,1,1,2], d⊤=[3,4,5,2,5,6,6,1,1,2])
BiCM{Nothing, Float64} (10 + 10 vertices, 3 + 6 unique degrees, 0.45 compression ratio)

```

```jldoctest
# generating a model directly from a degree sequence with a different precision
julia> model = model = BiCM(d⊥=[1,1,2,2,2,3,3,1,1,2], d⊤=[3,4,5,2,5,6,6,1,1,2], precision=Float32)
BiCM{Nothing, Float32} (10 + 10 vertices, 3 + 6 unique degrees, 0.45 compression ratio)

```

```jldoctest
# generating a model from an adjacency matrix
julia> A = [0 0 0 1 0;0 0 0 1 0;0 0 0 0 1;1 1 0 0 0;0 0 1 0 0];

julia> G = MaxEntropyGraphs.Graphs.SimpleGraph(A);

julia> @assert MaxEntropyGraphs.Graphs.is_bipartite(G); # check if the graph is bipartite

julia> model = BiCM(G) # generating the model
BiCM{Graphs.SimpleGraphs.SimpleGraph{Int64}, Float64} (3 + 2 vertices, 1 + 2 unique degrees, 0.60 compression ratio)

```

```jldoctest
# generating a model from a biadjacency matrix
julia> biadjacency = [1 0;1 0; 0 1];

julia> N⊥,N⊤ = size(biadjacency); # layer dimensions

julia> adjacency = [zeros(Int, N⊥,N⊥) biadjacency; biadjacency' zeros(Int,N⊤,N⊤)];

julia> G = MaxEntropyGraphs.Graphs.SimpleGraph(adjacency); # generate graph

julia> model = BiCM(G) # generate model
BiCM{Graphs.SimpleGraphs.SimpleGraph{Int64}, Float64} (3 + 2 vertices, 1 + 2 unique degrees, 0.60 compression ratio)

```

```jldoctest
# generating a model from an edge list
julia> edges = MaxEntropyGraphs.Graphs.SimpleEdge.([(1,4); (2,4); (3,5)]);

julia> G = MaxEntropyGraphs.Graphs.SimpleGraph(edges); # generate graph

julia> model = BiCM(G) # generate model
BiCM{Graphs.SimpleGraphs.SimpleGraph{Int64}, Float64} (3 + 2 vertices, 1 + 2 unique degrees, 0.60 compression ratio)

```
