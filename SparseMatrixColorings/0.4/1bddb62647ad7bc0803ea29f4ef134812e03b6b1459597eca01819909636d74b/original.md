```
fast_coloring(
    S::AbstractMatrix,
    problem::ColoringProblem,
    algo::GreedyColoringAlgorithm;
    [symmetric_pattern=false]
)
```

Solve a [`ColoringProblem`](@ref) on the matrix `S` with a [`GreedyColoringAlgorithm`](@ref) and return

  * a single color vector for `:column` and `:row` problems
  * a tuple of color vectors for `:bidirectional` problems

This function is very similar to [`coloring`](@ref), but it skips the computation of an [`AbstractColoringResult`](@ref) to speed things up.

# See also

  * [`coloring`](@ref)
