```
function apply_voltage_angle_difference_bounds!(
    pmitd_data::Dict{String,<:Any},
    vad::Real=5.0
)
```

Applies the corresponding transformation of voltage angle difference bound given by `vad::Real` in degrees (*i.e.*, the allowed drift of angle from one end of a line to another) to all lines, to the `pmd` dictionary.
