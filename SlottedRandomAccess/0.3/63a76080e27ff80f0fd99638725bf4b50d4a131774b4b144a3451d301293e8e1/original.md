```
simulate!(sim::PLR_Simulation; kwargs...)
```

Perform the simulation to compute the PLR for each load point in the `PLR_Simulation` object, using all available threads by default. The function sends a warning if julia is started with a single thread

!!! note
    Points that already contain valid simulation results are skipped and a new simulation object must be explicitly created to recompute them.


# Keyword Arguments

  * `logger`: The logger to use for displaying the progress of the simulation. Defaults to the default julia logger and also prints to the terminal via TerminalLogger.jl when executed from an interactive julia session (i.e. the REPL).
  * `ntasks`: The number of tasks to use for the parallel computation of each PLR point. Uses all available threads if not provided.
