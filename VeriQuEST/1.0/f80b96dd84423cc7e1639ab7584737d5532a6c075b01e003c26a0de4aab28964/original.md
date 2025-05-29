```
add_noise!(client::Client, noise_model::NoiseModel)
```

This function adds noise to a quantum system according to the specified noise model. It calls the `add_noise!` function  with a new client and the given noise model as arguments.

# Arguments

  * `client::Client`: The client for which the noise is being added.
  * `noise_model::NoiseModel`: The noise model to be used.

# Examples

```julia
client = Client()
noise_model = NoiseModel()
add_noise!(client, noise_model)
```
