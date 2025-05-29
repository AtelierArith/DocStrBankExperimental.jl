```
ESN(train_data; kwargs...) -> ESN
```

Creates an Echo State Network (ESN).

# Arguments

  * `train_data`: Matrix of training data `num_features x time_steps`.
  * `variation`: Variation of ESN (default: `Default()`).
  * `input_layer`: Input layer of ESN.
  * `reservoir`: Reservoir of the ESN.
  * `bias`: Bias vector for each time step.
  * `rng`: Random number generator used for initializing weights. Default is `Utils.default_rng()`.
  * `reservoir_driver`: Mechanism for evolving reservoir states (default: `RNN()`).
  * `nla_type`: Non-linear activation type (default: `NLADefault()`).
  * `states_type`: Format for storing states (default: `StandardStates()`).
  * `washout`: Initial time steps to discard (default: `0`).
  * `matrix_type`: Type of matrices used internally (default: type of `train_data`).

# Examples

```jldoctest
julia> train_data = rand(Float32, 10, 100)  # 10 features, 100 time steps
10×100 Matrix{Float32}:
 0.567676   0.154756  0.584611  0.294015   …  0.573946    0.894333    0.429133
 0.327073   0.729521  0.804667  0.263944      0.559342    0.020167    0.897862
 0.453606   0.800058  0.568311  0.749441      0.0713146   0.464795    0.532854
 0.0173253  0.536959  0.722116  0.910328      0.00224048  0.00202501  0.631075
 0.366744   0.119761  0.100593  0.125122      0.700562    0.675474    0.102947
 0.539737   0.768351  0.54681   0.648672   …  0.256738    0.223784    0.94327
 0.558099   0.42676   0.1948    0.735625      0.0989234   0.119342    0.624182
 0.0603135  0.929999  0.263439  0.0372732     0.066125    0.332769    0.25562
 0.4463     0.334423  0.444679  0.311695      0.0494497   0.27171     0.214925
 0.987182   0.898593  0.295241  0.233098      0.789699    0.453692    0.759205

julia> esn = ESN(train_data, 10, 300; washout=10)
ESN(10 => 300)
```
