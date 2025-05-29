```julia
struct SetCovering{ET, T, WT<:AbstractArray{T, 1}} <: ProblemReductions.ConstraintSatisfactionProblem{T}
```

The Set Covering problem is defined as follow: given a universe of elements and a collection of subsets of the universe, each set is associated with a weight.  The goal is to find a subset of sets that covers all the elements with the minimum total weight.

## Positional arguments

  * `elements` is a vector of elements in the universe.
  * `sets` is a vector of vectors, a collection of subsets of universe , each set is associated with a weight specified in `weights`.
  * `weights` are associated with sets.

## Example

In the following example, we solve a Set Covering problem with 3 subsets and weights `[1,2,3]`.

```jldoctest
julia> using ProblemReductions

julia> subsets = [[1, 2, 3], [2, 4], [1, 4]]
3-element Vector{Vector{Int64}}:
 [1, 2, 3]
 [2, 4]
 [1, 4]

julia> weights = [1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> setcovering = SetCovering(subsets, weights)
SetCovering{Int64, Int64, Vector{Int64}}([1, 2, 3, 4], [[1, 2, 3], [2, 4], [1, 4]], [1, 2, 3])

julia> num_variables(setcovering)  # degrees of freedom
3

julia> solution_size(setcovering, [1, 0, 1])  # size of a configuration
SolutionSize{Int64}(4, true)

julia> solution_size(setcovering, [0, 1, 1])
SolutionSize{Int64}(5, false)

julia> sc = set_weights(setcovering, [1, 2, 3])  # set the weights of the subsets
SetCovering{Int64, Int64, Vector{Int64}}([1, 2, 3, 4], [[1, 2, 3], [2, 4], [1, 4]], [1, 2, 3])
```
