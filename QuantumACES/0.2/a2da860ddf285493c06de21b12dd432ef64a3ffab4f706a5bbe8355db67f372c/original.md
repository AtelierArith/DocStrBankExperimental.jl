```
rand_design_filename(d_rand::RandDesign)
rand_design_filename(d::Design, total_randomisations::Integer, seed::UInt64)
rand_design_filename(circuit_param::AbstractCircuitParameters, noise_param::AbstractNoiseParameters, tuple_number::Integer, repeat_numbers::Vector{Int}, full_covariance::Bool, ls_type::Symbol, total_randomisations::Integer, seed::UInt64)
```

Returns a string describing the filename corresponding to the randomised design data.
