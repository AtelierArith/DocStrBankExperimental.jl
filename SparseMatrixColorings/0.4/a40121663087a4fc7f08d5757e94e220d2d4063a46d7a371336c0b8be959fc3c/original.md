```
AbstractColoringResult{structure,partition,decompression}
```

Abstract type for the result of a coloring algorithm.

It is the supertype of the object returned by the main function [`coloring`](@ref).

# Type parameters

Combination between the type parameters of [`ColoringProblem`](@ref) and [`GreedyColoringAlgorithm`](@ref):

  * `structure::Symbol`: either `:nonsymmetric` or `:symmetric`
  * `partition::Symbol`: either `:column`, `:row` or `:bidirectional`
  * `decompression::Symbol`: either `:direct` or `:substitution`

# Applicable methods

  * [`column_colors`](@ref) and [`column_groups`](@ref) (for a `:column` or `:bidirectional` partition)
  * [`row_colors`](@ref) and [`row_groups`](@ref) (for a `:row` or `:bidirectional` partition)
  * [`sparsity_pattern`](@ref)
  * [`compress`](@ref), [`decompress`](@ref), [`decompress!`](@ref), [`decompress_single_color!`](@ref)

!!! warning
    Unlike the methods above, the concrete subtypes of `AbstractColoringResult` are not part of the public API and may change without notice.

