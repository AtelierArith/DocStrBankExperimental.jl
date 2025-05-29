```
create_states(reservoir_driver::AbstractReservoirDriver, train_data, washout,
    reservoir_matrix, input_matrix, bias_vector)
```

Create and return the trained Echo State Network (ESN) states according to the specified reservoir driver.

# Arguments

  * `reservoir_driver`: The reservoir driver that determines how the ESN states evolve over time.
  * `train_data`: The training data used to train the ESN.
  * `washout`: The number of initial time steps to discard during training to allow the reservoir dynamics to wash out the initial conditions.
  * `reservoir_matrix`: The reservoir matrix representing the dynamic, recurrent part of the ESN.
  * `input_matrix`: The input matrix that defines the connections between input features and reservoir nodes.
  * `bias_vector`: The bias vector to be added at each time step during the reservoir update.
