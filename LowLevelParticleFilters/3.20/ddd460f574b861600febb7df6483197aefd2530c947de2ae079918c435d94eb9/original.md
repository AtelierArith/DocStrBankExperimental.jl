```
update!(imm::IMM, u, y, p, t; correct_kwargs = (;), predict_kwargs = (;), interact = true)
```

The combined udpate for an [`IMM`](@ref) filter performs the following steps:

1. Correct each model with the measurements `y` and control input `u`.
2. Combine the models into a single state and covariance.
3. Interact the models to update their respective state and covariance.
4. Predict each model to the next time step.

This differs slightly from the udpate step of other filters, where at the end of an update the state of the filter is the one-step ahead *predicted* value, whereas here each individual filter has a predicted state, but the [`combine!`](@ref) step of the IMM filter hasn't been performed on the predictions yet. The state of the IMM filter is thus $x(t|t)$ and not $x(t+1|t)$ like it is for other filters, and each filter internal to the IMM.

# Arguments:

  * `correct_kwargs`: An optional named tuple of keyword arguments that are sent to [`correct!`](@ref).
  * `predict_kwargs`: An optional named tuple of keyword arguments that are sent to [`predict!`](@ref).
  * `interact`: Whether or not to run the interaction step.
