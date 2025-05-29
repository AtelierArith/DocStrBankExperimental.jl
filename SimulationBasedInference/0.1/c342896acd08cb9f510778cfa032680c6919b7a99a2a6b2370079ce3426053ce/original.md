```
init(::SimulatorInferenceProblem, ::EKS, ensemble_alg; kwargs...)
```

Initializes EKS for the given `SimulatorInferenceProblem` using the Ensemble Kalman Sampling algorithm. This method automatically constructs an `EnsembleKalmanProcess` from the given inference problem and `named_data` pairs. If `initial_ens` is not provided, the initial ensemble is sampled from the prior.
