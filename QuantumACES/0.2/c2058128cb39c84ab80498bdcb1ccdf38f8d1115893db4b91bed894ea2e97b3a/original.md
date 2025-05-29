```
LognormalParameters
```

Parameterises a log-normally random Pauli noise model.

# Fields

  * `params::Dict{Symbol, Any}`: Dictionary of the noise parameters described below.
  * `noise_name::String`: Noise parameter name for saving data.

# Parameters

  * `r_1::Float64`: Average single-qubit gate entanglement infidelity, the sum of all 3 non-identity Pauli error probabilities.
  * `r_2::Float64`: Average two-qubit gate entanglement infidelity, the sum of all 15 non-identity Pauli error probabilities.
  * `r_m::Float64`: Average measurement error probability.
  * `r_im::Float64`: Average mid-circuit measurement idle entanglement infidelity.
  * `r_r::Float64`: Average mid-circuit reset error probability.
  * `r_1_std_log::Float64`: Approximate standard deviation of the logarithm of the single-qubit gate entanglement infidelity.
  * `r_2_std_log::Float64`: Approximate standard deviation of the logarithm of the two-qubit gate entanglement infidelity.
  * `r_m_std_log::Float64`: Approximate standard deviation of the logarithm of the measurement error probability.
  * `r_im_std_log::Float64`: Approximate standard deviation of the logarithm of the mid-circuit measurement idle entanglement infidelity.
  * `r_r_std_log::Float64`: Approximate standard deviation of the logarithm of the mid-circuit reset error probability.
  * `seed::UInt64`: Random seed used to generate the noise.
  * `combined::Bool`: Whether to treat Pauli X, Y, and Z basis SPAM noise as the same.
