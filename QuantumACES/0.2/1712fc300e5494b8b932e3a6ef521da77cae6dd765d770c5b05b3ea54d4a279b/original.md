```
DepolarisingParameters
```

Parameterises a depolarising Pauli noise model.

# Fields

  * `params::Dict{Symbol, Any}`: Dictionary of the noise parameters described below.
  * `noise_name::String`: Noise parameter name for saving data.

# Parameters

  * `r_1::Real`: Single-qubit gate entanglement infidelity, the sum of all 3 non-identity Pauli error probabilities.
  * `r_2::Real`: Two-qubit gate entanglement infidelity, the sum of all 15 non-identity Pauli error probabilities.
  * `r_m::Real`: Measurement error probability.
  * `r_im::Real`: Mid-circuit measurement idle entanglement infidelity.
  * `r_r::Real`: Mid-circuit reset error probability.
  * `combined::Bool`: Whether to treat Pauli X, Y, and Z basis SPAM noise as the same.
