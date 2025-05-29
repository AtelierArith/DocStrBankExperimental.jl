```
estimatemse(circ, pstr::PauliString, n_mcsamples::Integer, thetas=π; stateoverlapfunc=overlapwithzero, circuit_is_reversed=false, customtruncfunc=nothing)
```

Function to estimate the mean square error of a truncated circuit simulation using Monte Carlo sampling. Returns the mean squared error of the truncated Pauli propagation simulation averaged over the `thetas`∈ [theta, theta] of the angle `theta` of each `PauliRotation`. Currently, the function only supports circuits with `PauliRotation` and `CliffordGate` gates.

The length the `thetas` vector should be equal to the number of parametrized gates in the circuit.  Alternatively, `thetas` can be a single real number applicable for all parametrized gates. The default `thetas=π` or any other non-array values assume that the circuit consists only of `PauliRotation` -`CliffordGate`. For `PauliRotation`, the value should be the integration range of the parameters around zero.

An initial state overlap function `stateoverlapfunc` can be provided to calculate the overlap of the backpropagated Pauli strings with the initial state. Importantly, the `kwargs` can be used to set the truncation parameters of the Pauli propagation. Currently supported are `max_weight`, `max_freq`, and `max_sins`. Note that `min_abs_coeff` is not supported here, as we consider errors integrated over the angles. `max_freq` effectively truncates small coefficients below (1/2)^`max_freq` on average over `thetas ∈ [-π, π]`. A custom truncation function can be passed as `customtruncfunc` with the signature `customtruncfunc(pstr::PauliStringType, coefficient)::Bool`.
