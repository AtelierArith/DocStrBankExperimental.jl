```
ManifoldCachedObjective{E,P,O<:AbstractManifoldObjective{<:E},C<:NamedTuple{}} <: AbstractDecoratedManifoldObjective{E,P}
```

Create a cache for an objective, based on a `NamedTuple` that stores some kind of cache.

# Constructor

```
ManifoldCachedObjective(M, o::AbstractManifoldObjective, caches::Vector{Symbol}; kwargs...)
```

Create a cache for the [`AbstractManifoldObjective`](@ref) where the Symbols in `caches` indicate, which function evaluations to cache.

# Supported symbols

| Symbol                      | Caches calls to (incl. `!` variants)           | Comment                   |
|:--------------------------- |:---------------------------------------------- |:------------------------- |
| `:Cost`                     | [`get_cost`](@ref)                             |                           |
| `:EqualityConstraint`       | [`get_equality_constraint`](@ref)`(M, p, i)`   |                           |
| `:EqualityConstraints`      | [`get_equality_constraint`](@ref)`(M, p, :)`   |                           |
| `:GradEqualityConstraint`   | [`get_grad_equality_constraint`](@ref)         | tangent vector per (p,i)  |
| `:GradInequalityConstraint` | [`get_inequality_constraint`](@ref)            | tangent vector per (p,i)  |
| `:Gradient`                 | [`get_gradient`](@ref)`(M,p)`                  | tangent vectors           |
| `:Hessian`                  | [`get_hessian`](@ref)                          | tangent vectors           |
| `:InequalityConstraint`     | [`get_inequality_constraint`](@ref)`(M, p, j)` |                           |
| `:InequalityConstraints`    | [`get_inequality_constraint`](@ref)`(M, p, :)` |                           |
| `:Preconditioner`           | [`get_preconditioner`](@ref)                   | tangent vectors           |
| `:ProximalMap`              | [`get_proximal_map`](@ref)                     | point per `(p,λ,i)`       |
| `:StochasticGradients`      | [`get_gradients`](@ref)                        | vector of tangent vectors |
| `:StochasticGradient`       | [`get_gradient`](@ref)`(M, p, i)`              | tangent vector per (p,i)  |
| `:SubGradient`              | [`get_subgradient`](@ref)                      | tangent vectors           |
| `:SubtrahendGradient`       | [`get_subtrahend_gradient`](@ref)              | tangent vectors           |

# Keyword arguments

  * `p=rand(M)`: the type of the keys to be used in the caches. Defaults to the default representation on `M`.
  * `value=get_cost(M, objective, p)`: the type of values for numeric values in the cache
  * `X=zero_vector(M,p)`: the type of values to be cached for gradient and Hessian calls.
  * `cache=[:Cost]`: a vector of symbols indicating which function calls should be cached.
  * `cache_size=10`: number of (least recently used) calls to cache
  * `cache_sizes=Dict{Symbol,Int}()`: a named tuple or dictionary specifying the sizes individually for each cache.
