```
is_vector(M::AbstractManifold, p, X, check_base_point::Bool=true; error::Symbol=:none, kwargs...)
is_vector(M::AbstractManifold, p, X, check_base_point::Bool=true, throw_error::Boolean; kwargs...)
```

Return whether `X` is a valid tangent vector at point `p` on the [`AbstractManifold`](@ref) `M`. Returns either `true` or `false`.

If `check_base_point` is set to true, this function also (first) calls [`is_point`](@ref) on `p`. Then, the function calls [`check_vector`](@ref) and checks whether the returned value is `nothing` or an error.

How to report a potential error can be set using the `error=` keyword

  * `:error`          - throws an error if `X` is not a tangent vector and/or `p` is not point

^ `:info`           - displays the error message as an `@info`

  * `:warn`           - displays the error message as a `@warn`ing.
  * `:none`           - (default) the function just returns `true`/`false`

all other symbols are equivalent to `error=:none`

The second signature is a shorthand, where `throw_error` is used for `error=:error` (`true`) and `error=:none` (default, `false`). This case ignores the `error=` keyword.
