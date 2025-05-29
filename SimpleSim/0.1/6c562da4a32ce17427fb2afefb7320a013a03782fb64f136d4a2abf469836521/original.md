```
@call_ct! model u
```

This macro should be used instead of `@call!` for calling the continuous-time dynamics of a hybrid model. This prevents ambiguity. See [`@call!`](@ref).
