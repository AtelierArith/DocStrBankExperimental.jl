```julia
debug_system(sys)

```

Replace functions with singularities with a function that errors with symbolic information. E.g.

```julia-repl
julia> sys = debug_system(sys);

julia> prob = ODEProblem(sys, [], (0, 1.0));

julia> du = zero(prob.u0);

julia> prob.f(du, prob.u0, prob.p, 0.0)
ERROR: DomainError with (-1.0,):
log errors with input(s): -cos(Q(t)) => -1.0
Stacktrace:
  [1] (::ModelingToolkit.LoggedFun{typeof(log)})(args::Float64)
  ...
```
