```
ValidationLieGroup{L<:AbstractLieGroup} <: AbstractLieGroup
```

A Lie group to add tests to input parameters and output values of functions defined for [`LieGroups`](@ref).

Using the `ignore_contexts` keyword allows to specify a single `Symbol` or a vector of `Symbols` Of which contexts to ignore.

Current contexts are

  * `:All`: disable all checks
  * `:Point`: checks for points
  * `:Algebra`: checks related to the [`LieAlgebra`](@ref)
  * `:Output`: checks for output
  * `:Input`: checks for input variables

# Fields

  * `lie_group::L` the [`AbstractLieGroup`](@ref) to be decorated
  * `mode::Symbol`: The mode to be used for error handling, either `:error` or `:warn`
  * `ignore_contexts::AbstractVector{Symbol}`: store contexts to be ignored of validation.
  * `ignore_functions::Dict{<:Function,<:Union{Symbol,<:AbstractVector{Symbol}}`: store contexts to be ignored with in a function or its mutating variant.

where all but the first field are analogous to the setups of the [`ValidationManifold`](@extref `ManifoldsBase.ValidationManifold`). We refer to those docs for more examples on their meaning.

# Constructor

```
ValidationLieGroup(L::AbstractLieGroup, check_manifold=true; kwargs...)
```

Generate the Validation Lie Group for the given [`AbstractLieGroup`](@ref) `L`. If `check_manifold` is set to `true` the inner manifold is additionally wrapped in a [`ValidationManifold`](@extref `ManifoldsBase.ValidationManifold`). All suitable keywords are passed to the constructor of the validation manifold as well.

# Keyword arguments

  * `error::Symbol=:error`: specify how errors in the validation should be reported. this is passed to [`is_point`](@extref `ManifoldsBase.is_point`) and [`is_vector`](@extref `ManifoldsBase.is_vector`) as the `error` keyword argument. Available values are `:error`, `:warn`, `:info`, and `:none`. Every other value is treated as `:none`.
  * `ignore_contexts = Vector{Symbol}()` a vector to indicate which validation contexts should not be performed.
  * `ignore_functions=Dict{Function,Union{Symbol,Vector{Symbol}}}()` a dictionary to disable certain contexts within functions. The key here is the non-mutating function variant (if it exists). The contexts are the same as in `ignore_contexts`.
