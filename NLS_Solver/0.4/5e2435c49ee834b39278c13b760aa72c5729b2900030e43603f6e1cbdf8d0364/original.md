```julia
abstract type Abstract_Solver_Result end
```

This is the base type returned by the [`solve`](@ref) method. It contains the information related to the founded solution.

# Interface

  * [`converged`](@ref)
  * [`iteration_count`](@ref)
  * [`objective_value`](@ref)
  * [`solution`](@ref)

# Implementations

  * [`LevenbergMarquardt_Result`](@ref)
  * [`LevenbergMarquardt_BC_Result`](@ref)
