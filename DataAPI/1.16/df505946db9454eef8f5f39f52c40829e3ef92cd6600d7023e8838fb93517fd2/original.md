```
unwrap(x)
```

For a given scalar argument `x`, potentially "unwrap" it to return the base wrapped value. Useful as a generic API for wrapper types when the original value is needed.

The default definition just returns `x` itself, i.e. no unwrapping is performned.

This generic function is owned by DataAPI.jl itself, which is the sole provider of the default definition.
