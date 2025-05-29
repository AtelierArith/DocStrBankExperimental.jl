```julia
struct SpinGlass{GT<:Graphs.AbstractGraph, T, WT<:AbstractArray{T, 1}} <: ProblemReductions.ConstraintSatisfactionProblem{T}
```

```
SpinGlass(graph::AbstractGraph, weights::AbstractVector)
SpinGlass(graph::SimpleGraph, J, h=zeros(nv(graph)))
```

Spin Glass is a type of disordered magnetic system that exhibits a glassy behavior. The Hamiltonian of the system on a simple graph $G=(V, E)$ is given by

$$
H(G, \sigma) = \sum_{(i,j) \in E} J_{ij} \sigma_i \sigma_j + \sum_{i \in V} h_i \sigma_i
$$

where $J_{ij} \in \mathbb{R}$ is the coupling strength between spins $i$ and $j$, $h_i \in \mathbb{R}$ is the external field on spin $i$, and $\sigma_i \in \{-1, 1\}$ is the spin variable. The configuration of a solution is specified by a binary variable in (0, 1), where 0 and 1 are mapped to spins -1 and 1, respectively.

This definition naturally extends to the case of a [`HyperGraph`](@ref):

$$
H(G, \sigma) = \sum_{e \in E} J_{e} \prod_k\sigma_k + \sum_{i \in V} h_i \sigma_i,
$$

where $J_e$ is the coupling strength associated with hyperedge $e$, and the product is over all spins in the hyperedge.

## Fields

  * `graph` is a graph object.
  * `J` are the coupling strengths associated with the edges.
  * `h` are the external fields associated with the vertices.

## Example

In the following example, we define a spin glass problem on a 4-vertex graph with given coupling strengths on edges and external fields on vertices.

```jldoctest
julia> using ProblemReductions, ProblemReductions.Graphs

julia> graph = SimpleGraph(Graphs.SimpleEdge.([(1, 2), (1, 3), (3, 4), (2, 3)]))
{4, 4} undirected simple Int64 graph

julia> J = [1, -1, 1, -1]  # coupling strength
4-element Vector{Int64}:
  1
 -1
  1
 -1

julia> h = [1, -1, -1, 1]  # external field
4-element Vector{Int64}:
  1
 -1
 -1
  1

julia> spinglass = SpinGlass(graph, J, h)  # Define a spin glass problem
SpinGlass{SimpleGraph{Int64}, Int64, Vector{Int64}}(SimpleGraph{Int64}(4, [[2, 3], [1, 3], [1, 2, 4], [3]]), [1, -1, 1, -1], [1, -1, -1, 1])

julia> num_variables(spinglass)  # degrees of freedom
4

julia> flavors(spinglass)  # flavors of the spins, 0 for up (+1), 1 for down (-1)
(0, 1)

julia> solution_size(spinglass, [1, 0, 0, 1])  # size of a configuration
SolutionSize{Int64}(-2, true)

julia> findbest(spinglass, BruteForce())  # solve the problem with brute force
1-element Vector{Vector{Int64}}:
 [1, 0, 1, 1]
```
