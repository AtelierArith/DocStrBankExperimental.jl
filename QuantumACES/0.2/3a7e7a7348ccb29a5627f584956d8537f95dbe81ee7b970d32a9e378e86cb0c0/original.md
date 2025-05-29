```
design_filename(d::Design)
design_filename(circuit_param::AbstractCircuitParameters, noise_param::AbstractNoiseParameters, tuple_number::Integer, repeat_numbers::Vector{Int}, full_covariance::Bool, ls_type::Symbol)
```

Returns a string describing the filename corresponding to the supplied design data.
