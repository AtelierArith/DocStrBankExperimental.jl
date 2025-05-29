```julia
# Specify the stiff ODE solver algorithm.
# `timestep` is the length of time for each splitting step.
SimulatorStrangSerial(stiffalg, timestep; stiff_kwargs...)
```

Perform a simulation using [Strang splitting](https://en.wikipedia.org/wiki/Strang_splitting), where the MTK system is assumed to be stiff and the operators are assumed to be non-stiff. The solution will be calculated in serial.

Additional kwargs for ODEProblem constructor:

  * u0: initial condtions; if "nothing", default values will be used.
  * p: parameters; if "nothing", default values will be used.

  * `stiffalg`: Stiff solver algorithm to use (see https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/)
  * `timestep`: Length of each splitting time step
  * `stiff_kwargs`: Keyword arguments for the stiff ODEProblem constructor and solver.
  * `alg`: Algoritm for performing gridded computations.

WARNING: Is is not possible to change the parameters using this strategy..
