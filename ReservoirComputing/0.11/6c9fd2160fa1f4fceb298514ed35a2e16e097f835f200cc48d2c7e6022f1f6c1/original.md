```
MRNN(activation_function, leaky_coefficient, scaling_factor)
MRNN(;activation_function=[tanh, sigmoid], leaky_coefficient=1.0,
    scaling_factor=fill(leaky_coefficient, length(activation_function)))
```

Returns a Multiple RNN (MRNN) initializer for the Echo State Network (ESN), introduced in [^Lun2015].

# Arguments

  * `activation_function`: A vector of activation functions used in the MRNN.
  * `leaky_coefficient`: The leaky coefficient used in the MRNN.
  * `scaling_factor`: A vector of scaling factors for combining activation functions.

# Keyword Arguments

  * `activation_function`: A vector of activation functions used in the MRNN. Defaults to `[tanh, sigmoid]`.
  * `leaky_coefficient`: The leaky coefficient used in the MRNN. Defaults to 1.0.
  * `scaling_factor`: A vector of scaling factors for combining activation functions. Defaults to an array of the same size as `activation_function` with all elements set to `leaky_coefficient`.

This function creates an MRNN object with the specified activation functions, leaky coefficient, and scaling factors, which can be used as a reservoir driver in the ESN.

[^Lun2015]: Lun, Shu-Xian, et al. "*A novel model of leaky integrator echo state network for time-series prediction.*" Neurocomputing 159 (2015): 58-66.
