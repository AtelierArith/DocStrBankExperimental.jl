```
@t8_adapt_callback(callback)
```

Wrap the Julia function `callback` in an `@cfunction` with the appropriate signature required for callback functions in [`t8_forest_adapt`](@ref).
