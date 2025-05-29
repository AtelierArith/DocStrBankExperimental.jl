```
DBCM(G::T; precision::N=Float64, kwargs...) where {T<:Graphs.AbstractGraph, N<:Real}
DBCM(;d_out::Vector{T}, d_in::Vector{T}, precision::Type{<:AbstractFloat}=Float64, kwargs...)
```

Constructor function for the `DBCM` type. 

By default and dependng on the graph type `T`, the definition of in- and outdegree from $Graphs.jl$ is applied.  If you want to use a different definition of degrees, you can pass vectors of degrees sequences as keyword arguments (`d_out`, `d_in`). If you want to generate a model directly from degree sequences without an underlying graph, you can simply pass the degree sequences as arguments (`d_out`, `d_in`). If you want to work from an adjacency matrix, or edge list, you can use the graph constructors from the $JuliaGraphs$ ecosystem.

# Examples

```jldoctest DBCM_creation
# generating a model from a graph
julia> G = MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques())
{16, 111} directed simple Int64 graph
julia> model = DBCM(G)
DBCM{Graphs.SimpleGraphs.SimpleDiGraph{Int64}, Float64} (16 vertices, 15 unique degree pairs, 0.94 compression ratio)
```

```jldoctest DBCM_creation
# generating a model directly from a degree sequence
julia> model = DBCM(d_out=MaxEntropyGraphs.Graphs.outdegree(G), d_in=MaxEntropyGraphs.Graphs.indegree(G))
DBCM{Nothing, Float64} (16 vertices, 15 unique degree pairs, 0.94 compression ratio)
```

```jldoctest DBCM_creation
# generating a model directly from a degree sequence with a different precision
julia>  model = DBCM(d_out=MaxEntropyGraphs.Graphs.outdegree(G), d_in=MaxEntropyGraphs.Graphs.indegree(G), precision=Float32)
DBCM{Nothing, Float32} (16 vertices, 15 unique degree pairs, 0.94 compression ratio)
```

```jldoctest DBCM_creation
# generating a model from an adjacency matrix
julia> A = [0 1 1;1 0 0;1 1 0];

julia> G = MaxEntropyGraphs.Graphs.SimpleDiGraph(A)
{3, 5} directed simple Int64 graph
julia> model = DBCM(G)
DBCM{Graphs.SimpleGraphs.SimpleDiGraph{Int64}, Float64} (3 vertices, 3 unique degree pairs, 1.00 compression ratio)
```

```jldoctest DBCM_creation
# generating a model from an edge list
julia> E = [(1,2),(1,3),(2,3)];

julia> edgelist = [MaxEntropyGraphs.Graphs.Edge(x,y) for (x,y) in E];

julia> G = MaxEntropyGraphs.Graphs.SimpleDiGraphFromIterator(edgelist)
{3, 3} directed simple Int64 graph
julia> model = DBCM(G)
DBCM{Graphs.SimpleGraphs.SimpleDiGraph{Int64}, Float64} (3 vertices, 3 unique degree pairs, 1.00 compression ratio)

```

See also [`Graphs.outdegree`](https://juliagraphs.org/Graphs.jl/stable/core_functions/core/#Graphs.outdegree-Tuple{AbstractGraph,%20Integer}), [`Graphs.indegree`](https://juliagraphs.org/Graphs.jl/stable/core_functions/core/#Graphs.indegree-Tuple{AbstractGraph,%20Integer}).
