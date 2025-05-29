```julia
struct DominatingSet{GT<:Graphs.AbstractGraph, T, WT<:AbstractArray{T, 1}} <: ProblemReductions.ConstraintSatisfactionProblem{T}
```

```
DominatingSet(graph::AbstractGraph, weights::AbstractVector=UnitWeight(ne(graph))) -> DominatingSet
```

Dominaing Set is a subset of vertices in a undirected graph such that all the vertices in the set are either in the dominating set or in its first-order neighborhood. The DominatingSet problem is to find the dominating set with minimum number of vertices.

## Fields

  * `graph` is the problem graph.
  * `weights::AbstractVector`: Weights associated with the vertices of the `graph`. Defaults to `UnitWeight(nv(graph))`.

## Example

In the following example, we define a dominating set problem on a path graph with five vertices. To define a `DominatingSet` problem, we need to specify the graph and possibily the weights associated with vertices. The weights are set as unit by default in the current version and might be generalized to arbitrary positive weights in the following development.

```jldoctest
julia> using ProblemReductions, Graphs

julia> graph = path_graph(5)
{5, 4} undirected simple Int64 graph

julia> DS = DominatingSet(graph)
DominatingSet{SimpleGraph{Int64}, Int64, UnitWeight}(SimpleGraph{Int64}(4, [[2], [1, 3], [2, 4], [3, 5], [4]]), [1, 1, 1, 1, 1])

julia> variables(DS)  # degrees of freedom
1:5

julia> flavors(DS)  # flavors of the vertices
(0, 1)

julia> solution_size(DS, [0, 1, 0, 1, 0]) # Positive sample: (size) of a dominating set
SolutionSize{Int64}(2, true)

julia> solution_size(DS, [0, 1, 1, 0, 0]) # Negative sample: number of vertices
SolutionSize{Int64}(2, false)

julia> findbest(DS, BruteForce())  # solve the problem with brute force
3-element Vector{Vector{Int64}}:
 [1, 0, 0, 1, 0]
 [0, 1, 0, 1, 0]
 [0, 1, 0, 0, 1]
```
