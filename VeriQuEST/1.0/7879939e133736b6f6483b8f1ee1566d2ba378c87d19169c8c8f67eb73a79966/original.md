```
add_noise!(server::NoisyServer, server_qureg)
```

Adds noise to a quantum register (`server_qureg`) based on the noise model(s) defined in a `NoisyServer`. The function supports both single and multiple noise models. For each noise model, it retrieves the parameters using `get_noise_model_params` and applies the noise to each qubit in the quantum register.

# Arguments

  * `server::NoisyServer`: A `NoisyServer` instance that contains the noise model(s) to be applied.
  * `server_qureg`: The quantum register to which the noise will be applied.

# Examples

```julia
server = NoisyServer(noise_model)
server_qureg = QuantumRegister(3)
add_noise!(server, server_qureg)
```
