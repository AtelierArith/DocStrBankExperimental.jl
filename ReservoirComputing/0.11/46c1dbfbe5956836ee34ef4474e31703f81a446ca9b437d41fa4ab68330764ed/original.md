```
RNN(activation_function, leaky_coefficient)
RNN(;activation_function=tanh, leaky_coefficient=1.0)
```

Returns a Recurrent Neural Network (RNN) initializer for echo state networks (`ESN`).

# Arguments

  * `activation_function`: The activation function used in the RNN.
  * `leaky_coefficient`: The leaky coefficient used in the RNN.

# Keyword Arguments

  * `activation_function`: The activation function used in the RNN. Defaults to `tanh_fast`.
  * `leaky_coefficient`: The leaky coefficient used in the RNN. Defaults to 1.0.
