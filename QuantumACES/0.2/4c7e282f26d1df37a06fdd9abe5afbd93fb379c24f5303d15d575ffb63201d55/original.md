```
load_aces(d::Design, budget_set::Vector{Int})
load_aces(circuit_param::AbstractCircuitParameters, noise_param::AbstractNoiseParameters, tuple_number::Integer, repeat_numbers::Vector{Int}, full_covariance::Bool, ls_type::Symbol, budget_set::Vector{Int})
```

Loads the ACES data whose filename is specified by the supplied variables.
