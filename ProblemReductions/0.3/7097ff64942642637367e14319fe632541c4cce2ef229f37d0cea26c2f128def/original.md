```julia
struct SetPacking{ET, T, WT<:AbstractArray{T, 1}} <: ProblemReductions.ConstraintSatisfactionProblem{T}
```

SetPacking(elements::AbstractVector, sets::AbstractVector, weights::AbstractVector=UnitWeight(length(sets))) -> SetPacking

A packing is a set of sets where each set is pairwise disjoint from each other. The maximum (weighted) packing problem is to find the maximum packing for a given union and a set of subsets.

## Fields

  * `elements` is a vector of elements in the universe.
  * `sets` is a vector of vectors, each set is associated with a weight specified in `weights`.
  * `weights` are associated with sets. Defaults to `UnitWeight(length(sets))`.

## Example

In the following example, we define a set packing problem with five subsets. To define a `SetPacking` problem, we need to specify the set of subsets and possibily the weights associated with these subsets. The weights are set as unit by default in the current version and might be generalized to arbitrary positive weights in the following development. Besides, the elements would be automatically counted by the construction function.

```jldoctest
julia> using ProblemReductions

julia> sets = [[1, 2, 5], [1, 3], [2, 4], [3, 6], [2, 3, 6]]
5-element Vector{Vector{Int64}}:
 [1, 2, 5]
 [1, 3]
 [2, 4]
 [3, 6]
 [2, 3, 6]

julia> SP = SetPacking(sets)
SetPacking{Int64, Int64, UnitWeight}([1, 2, 5, 3, 4, 6], [[1, 2, 5], [1, 3], [2, 4], [3, 6], [2, 3, 6]], [1, 1, 1, 1, 1])

julia> num_variables(SP)  # degrees of freedom
5

julia> flavors(SP)  # flavors of the subsets
(0, 1)

julia> solution_size(SP, [1, 0, 0, 1, 0]) # Positive sample: -(size) of a packing
SolutionSize{Int64}(2, true)

julia> solution_size(SP, [1, 0, 1, 1, 0]) # Negative sample: 0
SolutionSize{Int64}(3, false)

julia> findbest(SP, BruteForce())  # solve the problem with brute force
3-element Vector{Vector{Int64}}:
 [0, 1, 1, 0, 0]
 [1, 0, 0, 1, 0]
 [0, 0, 1, 1, 0]
```
