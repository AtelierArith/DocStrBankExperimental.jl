```
load_rand_design(d::Design, total_randomisations::Integer, seed::UInt64)
load_rand_design(circuit_param::AbstractCircuitParameters, noise_param::AbstractNoiseParameters, tuple_number::Integer, repeat_numbers::Vector{Int}, full_covariance::Bool, ls_type::Symbol, total_randomisations::Integer, seed::UInt64)
```

Loads the randomised experimental design whose filename is specified by the supplied variables.
