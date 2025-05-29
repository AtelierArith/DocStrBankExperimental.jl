```
exec(lk::Link, from::Link, f, args...; kwargs...)
exec(lk::Link, f, args...; timeout::Real=5.0, kwargs...)
exec(name::Symbol, ....)
```

Ask an actor `lk` (or `name` if registered) to execute an  arbitrary function and to send the returned value as  [`Response`](@ref).

# Arguments

  * actor `lk::Link` or `name::Symbol` if registered,
  * `from::Link`: the link a `Response` should be sent to.
  * `f`: a callable object,
  * `args...; kwargs...`: arguments and keyword arguments to it,
  * `timeout::Real=5.0`: timeout in seconds. Set `timeout=Inf`    if you don't want to timeout.

**Note:** If `from` is ommitted, `exec` blocks, waits and  returns the result (with a `timeout`).
