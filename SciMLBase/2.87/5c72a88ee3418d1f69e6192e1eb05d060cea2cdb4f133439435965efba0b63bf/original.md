```julia
NonlinearProblem(f, u0; ...)
NonlinearProblem(f, u0, p; kwargs...)

```

Define a nonlinear problem using an instance of [`AbstractODEFunction`](@ref AbstractODEFunction). Note that this is interpreted in the form of the steady state problem, i.e. find the ODE's solution at time $t = \infty$.
