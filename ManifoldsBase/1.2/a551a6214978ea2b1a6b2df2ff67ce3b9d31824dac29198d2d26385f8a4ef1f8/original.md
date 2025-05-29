```
is_point(M::AbstractManifold, p; error::Symbol = :none, kwargs...)
is_point(M::AbstractManifold, p, throw_error::Bool; kwargs...)
```

Return whether `p` is a valid point on the [`AbstractManifold`](@ref) `M`. By default the function calls [`check_point`](@ref), which returns an `ErrorException` or `nothing`.

How to report a potential error can be set using the `error=` keyword

  * `:error`          - throws an error if `p` is not a point
  * `:info`           - displays the error message as an `@info`
  * `:warn`           - displays the error message as a `@warning`
  * `:none` (default) – the function just returns `true`/`false`

all other symbols are equivalent to `error=:none`.

The second signature is a shorthand, where the boolean is used for `error=:error` (`true`) and `error=:none` (default, `false`). This case ignores the `error=` keyword
