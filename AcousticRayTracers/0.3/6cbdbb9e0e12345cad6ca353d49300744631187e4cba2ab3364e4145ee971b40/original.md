```
RaySolver(env; kwargs...)
```

Julia implementation of a ray/Gaussian beam propagation model. The model supports complex environments, but retains differentiability.

Supported keyword arguments:

  * `nbeams`: number of beams to use (default: 0, auto)
  * `min_angle`: minimum beam angle (default: -80°)
  * `max_angle`: maximum beam angle (default: 80°)
  * `ds`: nominal spacing between ray points (default: 1 m)
  * `atol`: absolute position tolerance (default: 0.0001 m)
  * `min_amplitude`: minimum ray amplitude to track (default: 1e-5)
  * `solver`: differential equation solver (default: nothing, auto)
  * `solver_tol`: solver tolerance (default: 1e-4)
