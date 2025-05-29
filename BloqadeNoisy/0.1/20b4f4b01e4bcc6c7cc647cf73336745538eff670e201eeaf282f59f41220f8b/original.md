```
function emulate
```

Emulate an ensemble and return the ensemble average of a set of expectation values

# Arguments

  * `prob`: NoisySchrodingerProblem
  * `ntraj`: Number of trajectories
  * `expectations`: Set of Hermitian operators representing observables. Matrix-like objects
  * `shots`: Whether to resample the solution at a fixed number of shots. No resamping if `shots = 0``
  * `report_error`: Returns 2σ estimated from the sample. Requires expectation values to be diagonal in computational basis
  * `ensemble_algo`: What type of parallelization is desired. See EnsembleSimulation documentation
