```julia
struct IndependentSet{GT<:Graphs.AbstractGraph, T, WT<:AbstractArray{T, 1}} <: ProblemReductions.ConstraintSatisfactionProblem{T}
```

```
IndependentSet(graph::AbstractGraph, weights::AbstractVector=UnitWeight(nv(graph))) -> IndependentSet
```

Independent Set is a subset of vertices in a undirected graph such that all the vertices in the set are not connected by edges (or called not adjacent). The maximum IndependentSet problem is to find the independent set with maximum number of vertices, which is a NP-complete problem. Let $G=(V, E)$ be a graph, and $w_v$ be the weight of vertex $v$. The energy based model of the independent set problem is:

$$
H(G, \mathbf{n}) = - \sum_{v \in V} w_v n_v + \sum_{(u, v) \in E} n_u n_v
$$

where $n_v$ is the number of vertices in the independent set, i.e. $n_v = 1$ if $v$ is in the independent set, and $n_v = 0$ otherwise. The larger the size of the independent set, the lower the energy.

## Fields

  * `graph::AbstractGraph`: The problem graph.
  * `weights::AbstractVector`: Weights associated with the vertices of the `graph`. Defaults to `UnitWeight(nv(graph))`.

## Example

In the following example, we define an independent set problem on a graph with four vertices. To define an `IndependentSet` problem, we need to specify the graph and possibily the weights associated with vertices. The weights are set as unit by default in the current version and might be generalized to arbitrary positive weights.

```jldoctest
julia> using ProblemReductions, Graphs

julia> graph = SimpleGraph(Graphs.SimpleEdge.([(1, 2), (1, 3), (3, 4), (2, 3)]))
{4, 4} undirected simple Int64 graph

julia> IS = IndependentSet(graph)
IndependentSet{SimpleGraph{Int64}, Int64, UnitWeight}(SimpleGraph{Int64}(4, [[2, 3], [1, 3], [1, 2, 4], [3]]), [1, 1, 1, 1])

julia> num_variables(IS)  # degrees of freedom
4

julia> flavors(IS)  # flavors of the vertices
(0, 1)

julia> solution_size(IS, [1, 0, 0, 1]) # Positive sample: -(size) of an independent set
SolutionSize{Int64}(2, true)

julia> solution_size(IS, [0, 1, 1, 0]) # Negative sample: 0
SolutionSize{Int64}(2, false)

julia> findbest(IS, BruteForce())  # solve the problem with brute force
2-element Vector{Vector{Int64}}:
 [1, 0, 0, 1]
 [0, 1, 0, 1]
```
