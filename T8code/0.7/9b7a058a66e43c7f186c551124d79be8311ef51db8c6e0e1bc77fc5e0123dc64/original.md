```
@t8_load_tree_data(callback)
```

Wrap the Julia function `callback` in an `@cfunction` with the appropriate signature required for callback functions in [`t8_geom_load_tree_data_fn`](@ref).
