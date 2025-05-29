```julia
mutable struct TestFunctionFactory{Tu, Tv}
```

Data structure containing DenseSystem used to calculate test functions for boundary flux calculations.

Type parameters:

  * `Tu`: value type of test functions
  * `Tv`: Default value type of system

      * `system::VoronoiFVM.AbstractSystem{Tv} where Tv`: Original system

  * `state::VoronoiFVM.SystemState{Tu, Tp, TMatrix, TGenericMatrix, TSolArray} where {Tu, Tp, TMatrix<:AbstractMatrix{Tu}, TGenericMatrix, TSolArray<:AbstractMatrix{Tu}}`: Test function system state

  * `control::VoronoiFVM.SolverControl`: Solver control
