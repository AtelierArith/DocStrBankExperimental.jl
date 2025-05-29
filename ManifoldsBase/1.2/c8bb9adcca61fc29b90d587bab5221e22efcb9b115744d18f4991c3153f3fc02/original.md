```
ValidationManifold{𝔽,M<:AbstractManifold{𝔽}} <: AbstractDecoratorManifold{𝔽}
```

A manifold to add tests to input and output values of functions defined in the interface.

Additionally the points and tangent vectors can also be encapsulated, cf. [`ValidationMPoint`](@ref), [`ValidationTangentVector`](@ref), and [`ValidationCotangentVector`](@ref). These types can be used to see where some data is assumed to be from, when working on manifolds where both points and tangent vectors are represented as (plain) arrays.

Using the `ignore_contexts` keyword allows to specify a single `Symbol` or a vector of `Symbols` Of which contexts to ignore.

Current contexts are

  * `:All`: disable all checks
  * `:Point`: checks for points
  * `:Vector`: checks for vectors
  * `:Output`: checks for output
  * `:Input`: checks for input variables

Using the `ignore_functions` keyword (dictionary) allows to disable/ignore certain checks within single functions for this manifold. The `key` of the dictionary has to be the `Function` to exclude something in. The `value` is either a single symbol or a vector of symbols with the same meaning as the `ignore_contexts` keyword, but limited to this function

# Examples

  * `exp => :All` disables *all* checks in the [`exp`](@ref) function
  * `exp => :Point` excludes point checks in the [`exp`](@ref) function
  * `exp => [:Point, :Vector]` excludes point and vector checks in the [`exp`](@ref) function

This manifold is a decorator for a manifold, i.e. it decorates a [`AbstractManifold`](@ref) `M` with types points, vectors, and covectors.

# Fields

  * `manifold::M`: The manifold to be decorated
  * `mode::Symbol`: The mode to be used for error handling, either `:error` or `:warn`
  * `ignore_contexts::AbstractVector{Symbol}`: store contexts to be ignored of validation.
  * `ignore_functions::Dict{<:Function,<:Union{Symbol,<:AbstractVector{Symbol}}`: store contexts to be ignored with in a function or its mutating variant.

# Constructors

```
ValidationManifold(M::AbstractManifold; kwargs...)
```

Generate the Validation manifold

```
ValidationManifold(M::AbstractManifold, V::ValidationManifold; kwargs...)
```

Generate the Validation manifold for `M` with the default values of `V`.

## Keyword arguments

  * `error::Symbol=:error`: specify how errors in the validation should be reported. this is passed to [`is_point`](@ref) and [`is_vector`](@ref) as the `error` keyword argument. Available values are `:error`, `:warn`, `:info`, and `:none`. Every other value is treated as `:none`.
  * `store_base_point::Bool=false`: specify whether or not to store the point `p` a tangent or cotangent vector is associated with. This can be useful for debugging purposes.
  * `ignore_contexts = Vector{Symbol}()` a vector to indicate which validation contexts should not be performed.
  * `ignore_functions=Dict{Function,Union{Symbol,Vector{Symbol}}}()` a dictionary to disable certain contexts within functions. The key here is the non-mutating function variant (if it exists). The contexts are thre same as in `ignore_contexts`.
