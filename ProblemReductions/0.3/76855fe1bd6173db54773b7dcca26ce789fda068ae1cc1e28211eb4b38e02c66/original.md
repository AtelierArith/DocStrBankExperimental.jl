```julia
struct MaximalIS{T, WT<:AbstractArray{T, 1}} <: ProblemReductions.ConstraintSatisfactionProblem{T}
```

Maximal independent set is a problem that very similar to the [`IndependentSet`](@ref) problem. The difference is that the solution space of a maximal indepdent set problem does not include the independent sets that can be extended by adding one more vertex.

## Fields

  * `graph` is the problem graph.
  * `weights` are associated with the vertices of the `graph`.

## Example

In the following example, we define a maximal independent set problem on a graph with four vertices. To define a `MaximalIS` problem, we need to specify the graph and possibily the weights associated with vertices. The weights are set as unit by default in the current version and might be generalized to arbitrary positive weights in the following development.

```jldoctest
julia> using ProblemReductions, Graphs

julia> graph = SimpleGraph(Graphs.SimpleEdge.([(1, 2), (1, 3), (3, 4), (2, 3), (1, 4)]))
{4, 5} undirected simple Int64 graph

julia> problem = MaximalIS(graph)
MaximalIS{Int64, UnitWeight}(SimpleGraph{Int64}(5, [[2, 3, 4], [1, 3], [1, 2, 4], [1, 3]]), [1, 1, 1, 1])

julia> num_variables(problem)  # degrees of freedom
4

julia> flavors(problem)
(0, 1)

julia> solution_size(problem, [0, 1, 0, 0])  # unlike the independent set, this configuration is not a valid solution
SolutionSize{Int64}(1, false)

julia> findbest(problem, BruteForce())
1-element Vector{Vector{Int64}}:
 [0, 1, 0, 1]
```
