```julia
struct PaintShop{LT} <: ProblemReductions.ConstraintSatisfactionProblem{Int64}
```

The binary paint shop problem is defined as follows: we are given a $2m$ length sequence containing $m$ cars, where each car appears twice. Each car need to be colored red in one occurrence, and blue in the other. We need to choose which occurrence for each car to color with which color — the goal is to minimize the number of times we need to change the current color.

## Fields

  * `sequence` is a vector of symbols, each symbol is associated with a color.
  * `isfirst` is a vector of boolean numbers, indicating whether the symbol is the first appearance in the sequence.

## Example

In the following example, we define a paint shop problem with 6 cars.

```jldoctest
julia> using ProblemReductions

julia> problem = PaintShop(["a","b","a","c","c","b"])
PaintShop{String}(["a", "b", "a", "c", "c", "b"], Bool[1, 1, 0, 1, 0, 0])

julia> num_variables(problem)
3

julia> flavors(problem)
(0, 1)

julia> solution_size(problem, [0, 1, 0])
SolutionSize{Int64}(4, true)

julia> findbest(problem, BruteForce())
2-element Vector{Vector{Int64}}:
 [1, 0, 0]
 [0, 1, 1]
```
