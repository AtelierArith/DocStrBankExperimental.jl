```
HEOMsolve(M, ρ0, tlist; e_ops, solver, H_t, params, verbose, filename, inplace, SOLVEROptions...)
heomsolve(M, ρ0, tlist; e_ops, solver, H_t, params, verbose, filename, inplace, SOLVEROptions...)
```

Solve the time evolution for auxiliary density operators based on ordinary differential equations.

# Parameters

  * `M::AbstractHEOMLSMatrix` : the matrix given from HEOM model
  * `ρ0::Union{QuantumObject,ADOs}` : system initial state (density matrix) or initial auxiliary density operators (`ADOs`)
  * `tlist::AbstractVector` : Denote the specific time points to save the solution at, during the solving process.
  * `e_ops::Union{Nothing,AbstractVector}`: List of operators for which to calculate expectation values.
  * `solver::OrdinaryDiffEqAlgorithm` : solver in package `DifferentialEquations.jl`. Default to `DP5()`.
  * `H_t::Union{Nothing,QuantumObjectEvolution}`: The time-dependent system Hamiltonian or Liouvillian. Default to `nothing`.
  * `params`: Parameters to pass to the solver. This argument is usually expressed as a `NamedTuple` or `AbstractVector` of parameters. For more advanced usage, any custom struct can be used.
  * `verbose::Bool` : To display verbose output and progress bar during the process or not. Defaults to `true`.
  * `filename::String` : If filename was specified, the ADOs at each time point will be saved into the JLD2 file "filename.jld2" after the solving process.
  * `inplace::Bool`: Whether to use the inplace version of the ODEProblem. Defaults to `true`.
  * `SOLVEROptions` : extra options for solver

# Notes

  * The [`ADOs`](@ref) will be saved depend on the keyword argument `saveat` in `kwargs`.
  * If `e_ops` is specified, the default value of `saveat=[tlist[end]]` (only save the final `ADOs`), otherwise, `saveat=tlist` (saving the `ADOs` corresponding to `tlist`). You can also specify `e_ops` and `saveat` separately.
  * The default tolerances in `kwargs` are given as `reltol=1e-6` and `abstol=1e-8`.
  * For more details about `solver` please refer to [`DifferentialEquations.jl` (ODE Solvers)](https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/)
  * For more details about `SOLVEROptions` please refer to [`DifferentialEquations.jl` (Keyword Arguments)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)

# Returns

  * sol::TimeEvolutionHEOMSol : The solution of the hierarchical EOM. See also [`TimeEvolutionHEOMSol`](@ref)

!!! note
    `heomsolve` is a synonym of `HEOMsolve`.

