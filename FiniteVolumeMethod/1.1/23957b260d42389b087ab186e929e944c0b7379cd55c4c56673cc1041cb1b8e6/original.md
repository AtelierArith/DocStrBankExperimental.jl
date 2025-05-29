```
SteadyFVMProblem(prob::AbstractFVMProblem)
```

This is a wrapper for an `AbstractFVMProblem` that indicates that the problem is to be solved as a steady-state problem.  You can then solve the problem using [`solve(::SteadyFVMProblem, ::Any; kwargs...)`](@ref) from NonlinearSolve.jl. Note that you  need to have set the final time to `Inf` if you want a steady state out at infinity rather than some finite actual time.

See also [`FVMProblem`](@ref) and [`FVMSystem`](@ref).
