```
become!(lk::Link, func, args1...; kwargs...)
become!(name::Symbol, ....)
```

Cause an actor to change behavior.

# Arguments

  * actor `lk::Link` (or `name::Symbol` if registered),
  * `func`: a callable object,
  * `args1...`: (partial) arguments to `func`,
  * `kwargs...`: keyword arguments to `func`.
