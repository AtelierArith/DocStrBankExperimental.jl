```
function emulate
```

Emulate the evolution of a noisy system by averaging over an ensemble of ntraj noisy trajectories. The output is an array where each array contains the output of output_func on the timeseries corresponding to a single trajectory.

# Arguments

  * `prob`: NoisySchrodingerProblem to emulate
  * `ntraj`: number of trajectories to use for simulation
  * `output_func`: Vector{Complex}->Any - Transformation of the statevector array to save
  * `ensemble_algo`: See EnsembleProblem documentation. Common choices are EnsembleSerial and EnsembleThreaded
