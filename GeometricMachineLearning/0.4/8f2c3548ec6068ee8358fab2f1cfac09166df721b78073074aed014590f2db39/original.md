```
iterate(nn, ics)
```

Iterate the neural network of type [`TransformerIntegrator`](@ref) for initial conditions `ics`.

The initial condition is a matrix $\in\mathbb{R}^{n\times\mathtt{seq\_length}}$ or `NamedTuple` of two matrices).

This function computes a trajectory for a Transformer that has already been trained for valuation purposes.

# Parameters

The following are optional keyword arguments:

  * `n_points::Int=100`: The number of time steps for which we run the prediction.
  * `prediction_window::Int=size(ics.q, 2)`: The prediction window (i.e. the number of steps we predict into the future) is equal to the sequence length (i.e. the number of input time steps) by default.
