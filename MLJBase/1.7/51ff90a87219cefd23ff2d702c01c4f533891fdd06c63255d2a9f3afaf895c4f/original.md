```
default_scitype_check_level()
```

Return the current global default value for scientific type checking when constructing machines.

```
default_scitype_check_level(i::Integer)
```

Set the global default value for scientific type checking to `i`.

The effect of the `scitype_check_level` option in calls of the form `machine(model, data, scitype_check_level=...)` is summarized below:

| `scitype_check_level` | Inspect scitypes? | If `Unknown` in scitypes | If other scitype mismatch |
|:--------------------- |:-----------------:|:------------------------:|:-------------------------:|
| 0                     |         ×         |                          |                           |
| 1 (value at startup)  |         ✓         |                          |          warning          |
| 2                     |         ✓         |         warning          |          warning          |
| 3                     |         ✓         |         warning          |           error           |
| 4                     |         ✓         |          error           |           error           |

See also [`machine`](@ref)
