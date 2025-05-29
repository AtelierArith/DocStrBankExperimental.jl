```julia
# Specify the number of threads and the stiff ODE solver algorithm.
# `timestep` is the length of time for each splitting step.
SimulatorStrangThreads(threads, stiffalg, timestep; stiff_kwargs...)
# Use the default number of threads.
SimulatorStrangThreads(stiffalg, timestep; stiff_kwargs...)
```

Perform a simulation using [Strang splitting](https://en.wikipedia.org/wiki/Strang_splitting), where the MTK system is assumed to be stiff and the operators are assumed to be non-stiff. The solution of the stiff ODE system is parallelized across grid cells using the specified number of threads.

  * `threads`: Number of threads to use
  * `stiffalg`: Stiff solver algorithm to use (see https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/)
  * `timestep`: Length of each splitting time step
  * `stiff_kwargs`: Keyword arguments for the stiff ODEProblem constructor and solver.
  * `alg`: Algoritm for performing gridded computations.
