```
seqd = discretize(seq::Sequence; sampling_params=default_sampling_params())
```

This function returns a sampled Sequence struct with RF and gradient time refinements based on simulation parameters.

# Arguments

  * `seq`: (`::Sequence`) sequence

# Keywords

  * `sampling_params`: (`::Dict{String, Any}`, `=default_sampling_params()`) sampling   parameter dictionary

# Returns

  * `seqd`: (`::DiscreteSequence`) DiscreteSequence struct
