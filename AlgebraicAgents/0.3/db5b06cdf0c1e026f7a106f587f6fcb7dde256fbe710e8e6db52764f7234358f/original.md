```
wrap_system(name, system, args...; kwargs...)
```

Typically, the function will dispatch on the type of `system` and initialise an algebraic agent which wraps the core dynamical system. This allows you to specify the core dynamics directly using a third-party package syntax and hide the internals on this package's side from the user.

For instance, you may define a method `wrap_system(name, prob::DiffEqBase.DEProblem)`, which internally will invoke the constructor of `DiffEqAgent`.

# Examples

```julia
wrap_system("ode_agent", ODEProblem(f, u0, tspan))
wrap_system("abm_agent", ABM(agent, space; properties))
```
