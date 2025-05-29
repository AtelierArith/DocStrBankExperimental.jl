```
get_voltage_min_mean_max(
    solution::Dict{String,<:Any},
    data::Dict{String,<:Any};
    make_per_unit::Bool=true
)::Tuple{Real,Real,Real}
```

Calculates the minimum, mean, and maximum of the voltages across a network (not a multinetwork)

`data` is used to convert the units to per*unit if `make*per*unit` and the data is not already per*unit.

If `make_per_unit` (default: true), will return voltage statistics in per-unit representation. If `make_per_unit` is false, and there are different voltage bases across the network, the statistics will not make sense.
