```
set_dim_units!(var::OutputVar, dim_name::AbstractString, units::AbstractString)
```

Set `units` for the `dim_name` dimension in `var`.

!!! warning "Override existing units"
    If units already exist for the dimension, this will override the units for the dimension in `var`.

