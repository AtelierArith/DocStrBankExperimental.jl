```
add_noise!(client::Client, model::Union{Damping,Dephasing,Depolarising,Pauli}, params::QubitNoiseParameters)
```

This function adds noise to a quantum system. The noise model can be one of Damping, Dephasing, Depolarising, or Pauli.  The function throws an error if the noise type is not SingleQubit. It then iterates over the range of qubits represented  in the backend and adds noise to each qubit according to the specified model and parameters.

# Arguments

  * `client::Client`: The client for which the noise is being added.
  * `model::Union{Damping,Dephasing,Depolarising,Pauli}`: The noise model to be used.
  * `params::QubitNoiseParameters`: The parameters for the noise model.

# Examples

```julia
client = Client()
model = Damping()
params = QubitNoiseParameters(SingleQubit(), backend)
add_noise!(client, model, params)
```
