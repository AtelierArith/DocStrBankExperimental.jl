```
Var.convert_dim_units(var, dim_name, new_units; conversion_function = nothing)
```

Return a new OutputVar with converted physical units of `dim_name` to `new_units` using `conversion_function`

This function does not support Unitful, so the parameter `conversion_function` must be supplied.
