```
EstimatedOutput(kf, prob, sym)
```

Create an output function that can be called like

```
g(x::Vector,    u, p, t)     # Compute an output
g(xR::MvNormal, u, p, t)     # Compute an output distribution given input distribution xR
g(kf,           u, p, t)     # Compute an output distribution given the current state of an AbstractKalmanFilter
```

# Arguments:

  * `kf`: A Kalman type filter
  * `prob`: A `StateEstimationProblem` object
  * `sym`: A symbolic expression or vector of symbolic expressions that the function should output.
