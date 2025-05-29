```
UBCM(G::T; d::Vector=Graphs.degree(G), precision::N=Float64, kwargs...) where {T<:Graphs.AbstractGraph, N<:Real}
UBCM(d::Vector{T}, precision::Type{<:AbstractFloat}=Float64, kwargs...)
```

Constructor function for the `UBCM` type. 

By default and dependng on the graph type `T`, the definition of degree from `Graphs.jl` is applied.  If you want to use a different definition of degree, you can pass a vector of degrees as the second argument. If you want to generate a model directly from a degree sequence without an underlying graph, you can simply pass the degree sequence as an argument. If you want to work from an adjacency matrix, or edge list, you can use the graph constructors from the `JuliaGraphs` ecosystem.

# Examples

```jldoctest
# generating a model from a graph
julia> G = MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate)
{34, 78} undirected simple Int64 graph
julia> model = UBCM(G)
UBCM{Graphs.SimpleGraphs.SimpleGraph{Int64}, Float64} (34 vertices, 11 unique degrees, 0.32 compression ratio)
```

```jldoctest
# generating a model directly from a degree sequence
julia> model = UBCM(d=[4;3;3;3;2])
UBCM{Nothing, Float64} (5 vertices, 3 unique degrees, 0.60 compression ratio)
```

```jldoctest
# generating a model directly from a degree sequence with a different precision
julia> model = UBCM(d=[4;3;3;3;2], precision=Float16)
UBCM{Nothing, Float16} (5 vertices, 3 unique degrees, 0.60 compression ratio)
```

```jldoctest
# generating a model from an adjacency matrix
julia> A = [0 1 1;1 0 0;1 0 0];

julia> G = MaxEntropyGraphs.Graphs.SimpleGraph(A)
{3, 2} undirected simple Int64 graph
julia> model = UBCM(G)
UBCM{Graphs.SimpleGraphs.SimpleGraph{Int64}, Float64} (3 vertices, 2 unique degrees, 0.67 compression ratio)
```

```jldoctest
# generating a model from an edge list
julia> E = [(1,2),(1,3),(2,3)];

julia> edgelist = [MaxEntropyGraphs.Graphs.Edge(x,y) for (x,y) in E];

julia> G = MaxEntropyGraphs.Graphs.SimpleGraphFromIterator(edgelist)
{3, 3} undirected simple Int64 graph
julia> model = UBCM(G)
UBCM{Graphs.SimpleGraphs.SimpleGraph{Int64}, Float64} (3 vertices, 1 unique degrees, 0.33 compression ratio)
```

See also [`Graphs.degree`](https://juliagraphs.org/Graphs.jl/stable/core_functions/core/#Graphs.degree), [`SimpleWeightedGraphs.inneighbors`](https://juliagraphs.org/SimpleWeightedGraphs.jl/stable/api/#Graphs.inneighbors-Tuple{SimpleWeightedDiGraph,%20Integer}).
