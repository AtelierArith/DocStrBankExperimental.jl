```
get_filter(prob::StateEstimationProblem, ::Type{ExtendedKalmanFilter}; constant_R1=true, kwargs)
get_filter(prob::StateEstimationProblem, ::Type{UnscentedKalmanFilter}; kwargs)
```

Instantiate a filter from a state-estimation problem. `kwargs` are sent to the filter constructor.

If `constant_R1=true`, the dynamics noise covariance matrix `R1` is assumed to be constant and is computed at the initial state. Otherwise, `R1` is computed at each time step throug repeated linearization w.r.t. the disturbance inputs `w`.
