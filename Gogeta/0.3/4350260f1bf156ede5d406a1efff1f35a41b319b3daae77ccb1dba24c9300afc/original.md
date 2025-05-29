```
function NN_compress(NN_model::Flux.Chain, U_in, L_in, U_bounds, L_bounds)
```

Compresses a neural network using precomputed bounds.

# Arguments

  * `NN_model`: Neural network to be compressed.
  * `U_in`: Upper bounds for the input variables.
  * `L_in`: Lower bounds for the input variables.
  * `U_bounds`: Upper bounds for the other neurons.
  * `L_bounds`: Lower bounds for the other neurons.

Returns a `Flux.Chain` model of the compressed neural network.
