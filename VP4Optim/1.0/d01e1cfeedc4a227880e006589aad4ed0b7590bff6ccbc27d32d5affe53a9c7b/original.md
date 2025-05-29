```
par!(mod::Model, new_par::AbstractArray)
```

Resets *all* fixed parameters by the values in `new_par`.

## Default

  * Copies the values from `new_par` into `val[par_ind]` (in this order).
  * Subsequently calls [par_changed!](@ref par_changed!) to trigger optional secondary actions.
  * Returns `nothing`.
