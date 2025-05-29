```
function emulate
```

Emulate an ensemble and return the ensemble average over bitstring distribution.

# Arguments

  * `prob`: NoisySchrodingerProblem
  * `ntraj`: Number of trajectories
  * `report_error`: Returns 2σ estimated from the sample
  * `ensemble_algo`: What type of parallelization is desired. See EnsembleSimulation documentation
