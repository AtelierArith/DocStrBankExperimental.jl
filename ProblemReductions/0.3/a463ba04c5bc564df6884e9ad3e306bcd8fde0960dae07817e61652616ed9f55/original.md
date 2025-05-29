```julia
struct MaxCut{T, WT<:AbstractArray{T, 1}} <: ProblemReductions.ConstraintSatisfactionProblem{T}
```

Max Cut problem is defined on weighted graphs. The goal is to find a partition of the vertices into two sets such that the sum of the weights of the edges between the two sets is maximized.

## Positional arguments

  * `graph` is the problem graph.
  * `weights` are associated with the edges of the `graph`. We have ensure that the `weights` are in the same order as the edges in `edges(graph)`.

## Example

In the following example, we solve a Max Cut problem on a complete graph with 3 vertices and edge weights `[1,2,3]`.

```jldoctest
julia> using ProblemReductions, Graphs

julia> g = complete_graph(3)
{3, 3} undirected simple Int64 graph

julia> maxcut = MaxCut(g,[1,2,3]) # specify the weights of the edges
MaxCut{Int64, Vector{Int64}}(SimpleGraph{Int64}(3, [[2, 3], [1, 3], [1, 2]]), [1, 2, 3])

julia> mc = set_weights(maxcut, [2,1,3]) # set the weights and get a new instance
MaxCut{Int64, Vector{Int64}}(SimpleGraph{Int64}(3, [[2, 3], [1, 3], [1, 2]]), [2, 1, 3])


julia> num_variables(maxcut) # return the number of vertices
3

julia> flavors(maxcut) # return the flavors of the vertices
(0, 1)

julia> solution_size(maxcut, [0,1,0]) # return the size of the configuration
SolutionSize{Int64}(4, true)

julia> findbest(maxcut, BruteForce()) # find the best configuration
2-element Vector{Vector{Int64}}:
 [1, 1, 0]
 [0, 0, 1]
```
