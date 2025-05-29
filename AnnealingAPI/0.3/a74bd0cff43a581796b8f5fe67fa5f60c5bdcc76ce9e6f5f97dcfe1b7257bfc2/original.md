```
rollback!(tracker, token)
```

Bring the system to the state before `update_corrfns!` was called. `token` must be an object returned by `update_corrfns!`.

See also: [`update_corrfns!`](@ref).
