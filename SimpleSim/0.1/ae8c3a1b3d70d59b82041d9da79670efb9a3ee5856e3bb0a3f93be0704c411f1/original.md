```
@call_dt! model u
```

This macro should be used instead of `@call!` for calling the discrete-time dynamics of a hybrid model. This prevents ambiguity. See [`@call!`](@ref).
