```
get_noise_model_params(model::Union{Damping,Dephasing,Depolarising,Pauli}, server_qureg::Union{DensityMatrix,Qureg})
```

Get the noise model parameters for a given noise model and server quantum register.

# Arguments

  * `model::Union{Damping,Dephasing,Depolarising,Pauli}`: The noise model to retrieve parameters for.
  * `server_qureg::Union{DensityMatrix,Qureg}`: The server quantum register.

# Returns

  * The noise parameters for the given noise model and server quantum register.

```
