```julia
mutable struct TestFunctionFactory
```

Data structure containing DenseSystem used to calculate test functions for boundary flux calculations.

  * `system::VoronoiFVM.AbstractSystem`: Original system

  * `tfsystem::VoronoiFVM.System{Tv, Tc, Ti, Tm, Matrix{Ti}, Matrix{Tv}} where {Tv, Tc, Ti, Tm}`: Test function system

  * `control::VoronoiFVM.SolverControl`: Solver control
