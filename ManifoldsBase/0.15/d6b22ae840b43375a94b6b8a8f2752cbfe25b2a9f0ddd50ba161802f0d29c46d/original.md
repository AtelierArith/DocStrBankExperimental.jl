```
isapprox(M::AbstractManifold, p, X, Y; error:Symbol=:none; kwargs...)
```

Check if vectors `X` and `Y` tangent at `p` from [`AbstractManifold`](@ref) `M` are approximately equal.

The optional positional argument can be used to get more information for the case that the result is false, if the concrete manifold provides such information. Currently the following are supported

  * `:error` - throws an error if `isapprox` evaluates to false, providing possibly a more detailed error. Note that this turns `isapprox` basically to an `@assert`.
  * `:info` – prints the information in an `@info`
  * `:warn` – prints the information in an `@warn`
  * `:none` (default) – the function just returns `true`/`false`

By default these informations are collected by calling [`check_approx`](@ref).

Keyword arguments can be used to specify tolerances.
