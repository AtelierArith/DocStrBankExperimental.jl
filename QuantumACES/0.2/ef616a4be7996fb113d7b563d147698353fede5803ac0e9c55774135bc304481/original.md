```
get_dep_param(r_1::Real, r_2::Real, r_m::Real)
get_dep_param(; r_1::Real, r_2::Real, r_m::Real, r_im::Real = r_m, r_r::Real = r_m)
```

Return a [`DepolarisingParameters`](@ref) object that parameterises a depolarising Pauli noise model.

# Arguments

  * `r_1::Real`: Single-qubit gate entanglement infidelity, the sum of all 3 non-identity Pauli error probabilities.
  * `r_2::Real`: Two-qubit gate entanglement infidelity, the sum of all 15 non-identity Pauli error probabilities.
  * `r_m::Real`: Measurement error probability.
  * `r_im::Real`: Mid-circuit measurement idle entanglement infidelity.
  * `r_r::Real`: Mid-circuit reset error probability.
  * `combined::Bool`: Whether to treat Pauli X, Y, and Z basis SPAM noise as the same.
