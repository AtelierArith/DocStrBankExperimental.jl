```
match_eltype(layer, ps, st, args...)
```

Helper function to "maybe" (see below) match the element type of `args...` with the element type of the layer's parameters and states. This is useful for debugging purposes, to track down accidental type-promotions inside Lux layers.

# Extended Help

## Controlling the Behavior via Preferences

Behavior of this function is controlled via the  `eltype_mismatch_handling` preference. The following options are supported:

  * `"none"`: This is the default behavior. In this case, this function is a no-op, i.e., it simply returns `args...`.
  * `"warn"`: This option will issue a warning if the element type of `args...` does not match the element type of the layer's parameters and states. The warning will contain information about the layer and the element type mismatch.
  * `"convert"`: This option is same as `"warn"`, but it will also convert the element type of `args...` to match the element type of the layer's parameters and states (for the cases listed below).
  * `"error"`: Same as `"warn"`, but instead of issuing a warning, it will throw an error.

!!! warning
    We print the warning for type-mismatch only once.


## Element Type Conversions

For `"convert"` only the following conversions are done:

| Element Type of parameters/states | Element Type of `args...` | Converted to |
|:--------------------------------- |:------------------------- |:------------ |
| `Float64`                         | `Integer`                 | `Float64`    |
| `Float32`                         | `Float64`                 | `Float32`    |
| `Float32`                         | `Integer`                 | `Float32`    |
| `Float16`                         | `Float64`                 | `Float16`    |
| `Float16`                         | `Float32`                 | `Float16`    |
| `Float16`                         | `Integer`                 | `Float16`    |
