```
par!(mod::Model, p_syms::AbstractArray, p_vals::AbstractArray)
```

Resets those fixed parameters, which are specified in `par_syms`, by the values in `p_vals`.

## Default

  * Copies the values from `p_vals` into the associated locations.
  * Subsequently calls [par_changed!](@ref par_changed!) to trigger optional secondary actions.
  * Returns `nothing`.
