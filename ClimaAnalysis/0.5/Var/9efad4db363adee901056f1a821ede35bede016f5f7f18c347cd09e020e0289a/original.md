```
set_units(var::OutputVar, units::AbstractString)
```

Set `units` for data in `var`.

!!! warning "Override existing units"
    If units already exist, this will override the units for data in `var`. To convert units, see [`Var.convert_units`](@ref)

