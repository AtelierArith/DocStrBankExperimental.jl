```
isapprox(M::AbstractManifold, p, q; error::Symbol=:none, kwargs...)
```

Check if points `p` and `q` from [`AbstractManifold`](@ref) `M` are approximately equal.

The keyword argument can be used to get more information for the case that the result is false, if the concrete manifold provides such information. Currently the following are supported

  * `:error` - throws an error if `isapprox` evaluates to false, providing possibly a more detailed error. Note that this turns `isapprox` basically to an `@assert`.
  * `:info` – prints the information in an `@info`
  * `:warn` – prints the information in an `@warn`
  * `:none` (default) – the function just returns `true`/`false`

Keyword arguments can be used to specify tolerances.
