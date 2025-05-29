```julia
solve(nls::AbstractNLS,
      θ_init::AbstractVector,
      conf::Abstract_Solver_Conf)::Abstract_Solver_Result
```

Generic interface to solve an [`AbstractNLS`](@ref) problem.

The used algorithm is defined through [`Abstract_Solver_Conf`](@ref) specializations.

The method returns a [`Abstract_Solver_Result`](@ref) specialization.
