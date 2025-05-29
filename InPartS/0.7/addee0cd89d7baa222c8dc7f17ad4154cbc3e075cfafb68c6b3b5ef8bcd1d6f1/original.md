```
evolve!(sim, tmax; kwargs...)
```

Evolve a `Simulation` for `tmax` time units, using [`computeforces!`](@ref) and [`propagate!`](@ref).

Returns a named tuple containing none of your business.

## Additional arguments

  * `tss::TimeSteppingStrategy` Set the time stepping strategy to use. Defaults to a [`FixedStepper`](@ref) with `dt = 1e-3`
  * `callback::AbstractCallback` Add a callback to the simulation.
  * `dontfinalize::Bool` If true, blocks execution of the callback finalizer. Use if you want to continue simulating on the same `Simulation`
  * `savedt::Bool` Include a list of timesteps `dt` in the return parameters. Not recommended except for debugging, defaults to `false`
