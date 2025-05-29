```
ChemPotBubbleTemperature(kwargs...)
```

Function to compute [`bubble_temperature`](@ref) via chemical potentials. It directly solves the equality of chemical potentials system of equations.

Inputs:

  * `y = nothing`: optional, initial guess for the vapor phase composition.
  * `T0 = nothing`: optional, initial guess for the bubble temperature [`K`].
  * `vol0 = nothing`: optional, initial guesses for the liquid and vapor phase volumes
  * `atol = 1e-8`: optional, absolute tolerance of the non linear system of equations
  * `rtol = 1e-12`: optional, relative tolerance of the non linear system of equations
  * `max_iters = 1000`: optional, maximum number of iterations
  * `nonvolatiles = nothing`: optional, Vector of strings containing non volatile compounds. those will be set to zero on the vapour phase.
