```
become(func, args...; kwargs...)
```

Cause your actor to take on a new behavior. This can only be called from inside an actor/behavior.

# Arguments

  * `func`: a callable object,
  * `args...`: (partial) arguments to `func`,
  * `kwargs...`: keyword arguments to `func`.
