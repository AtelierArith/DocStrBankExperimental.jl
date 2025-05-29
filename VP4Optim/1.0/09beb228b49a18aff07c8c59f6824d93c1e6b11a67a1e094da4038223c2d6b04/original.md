```
x!(mod::Model, new_x::AbstractArray)
```

Resets *all* variable parameters by the values in `new_x`.

## Default

  * Copies the values from `new_x` into `val[x_ind]` (in this order).
  * Subsequently calls [x_changed!](@ref x_changed!) to trigger optional secondary actions.
  * Returns `nothing`.
