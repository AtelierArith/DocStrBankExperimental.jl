```julia
struct Coloring{K, T, WT<:AbstractArray{T, 1}, OBJ} <: ProblemReductions.ConstraintSatisfactionProblem{T}
```

```
Coloring{K}(graph; weights=UnitWeight(nv(graph)), use_constraints::Bool=false)
```

The Vertex Coloring (Coloring) problem is defined on a simple graph. Given k kinds of colors, we need to determine whether we can color all vertices on the graph such that no two adjacent vertices share the same color.

## Fields

  * `graph` is the problem graph.
  * `weights` are associated with the edges of the `graph`, default to `UnitWeight(ne(graph))`.

## Example

To initialize a Coloring problem, we need to first define a graph and decide the number of colors.

```jldoctest
julia> using ProblemReductions, Graphs

julia> g = smallgraph(:petersen) # define a simple graph, petersen as example
{10, 15} undirected simple Int64 graph

julia> coloring = Coloring{3}(g)  # 3 colors
Coloring{3, Int64, UnitWeight, ProblemReductions.EXTREMA}(SimpleGraph{Int64}(15, [[2, 5, 6], [1, 3, 7], [2, 4, 8], [3, 5, 9], [1, 4, 10], [1, 8, 9], [2, 9, 10], [3, 6, 10], [4, 6, 7], [5, 7, 8]]), [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1])

julia> variables(coloring)
1:10

julia> flavors(coloring)
(0, 1, 2)

julia> is_vertex_coloring(coloring.graph,[1,2,3,1,3,2,1,2,3,1]) #random assignment
false
```
