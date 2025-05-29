```
add_noise!(model::Union{Damping,Dephasing,Depolarising,Pauli}, params::QubitNoiseParameters)
```

Add noise to a quantum model based on the given noise parameters.

# Arguments

  * `model::Union{Damping,Dephasing,Depolarising,Pauli}`: The quantum model to add noise to.
  * `params::QubitNoiseParameters`: The noise parameters specifying the type and strength of the noise.
