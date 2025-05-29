```
PlotData1D(sol; kwargs...)
```

Create a `PlotData1D` object from a solution object created by either `OrdinaryDiffEq.solve!` (which returns a `SciMLBase.ODESolution`) or Trixi.jl's own `solve!` (which returns a `TimeIntegratorSolution`).

!!! warning "Experimental implementation"
    This is an experimental feature and may change in future releases.

