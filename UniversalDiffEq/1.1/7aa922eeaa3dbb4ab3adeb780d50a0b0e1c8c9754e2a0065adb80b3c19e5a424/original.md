```
get_right_hand_side(UDE::UDE)
```

Returns the right-hand side of the differential equation (or difference equation) used to build the process model.

The function will take the state vector `u` and time `t` if the model does not include covariates. If covariates are included, then the arguments are the state vector `u` , covariates vector `x`, and time `t`.
