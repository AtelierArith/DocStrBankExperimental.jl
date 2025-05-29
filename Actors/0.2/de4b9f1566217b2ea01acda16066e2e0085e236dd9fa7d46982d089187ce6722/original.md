```
init!(lk::Link, f, args...; kwargs...)
init!(name::Symbol, ....)
```

Tell an actor `lk` to save the callable object `f` with the given  arguments as an `init` object in its [`_ACT`](@ref) variable.  The `init` object will be called by a supervisor at actor restart.

# Arguments

  * actor `lk::Link` or `name::Symbol` if registered,
  * `f`: callable object,
  * `args...`: arguments to `f`,
  * `kwargs...`: keyword arguments to `f`.
