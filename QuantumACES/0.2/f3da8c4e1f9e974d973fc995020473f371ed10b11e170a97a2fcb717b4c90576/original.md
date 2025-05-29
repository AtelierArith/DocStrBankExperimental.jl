```
scaling_filename(scaling_data::AbstractScalingData)
scaling_filename(d::Design, ls_type::Symbol)
scaling_filename(circuit_param::AbstractCircuitParameters, noise_param::AbstractNoiseParameters, tuple_number::Integer, repeat_numbers::Vector{Int}, ls_type::Symbol)
```

Returns a string describing the filename for the scaling data corresponding to the supplied design data.
