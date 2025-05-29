```
DynamicSS(alg = nothing; tspan = Inf)
```

Requires that an ODE algorithm is given as the first argument.  The absolute and relative tolerances specify the termination conditions on the derivative's closeness to zero.  This internally uses the `TerminateSteadyState` callback from the Callback Library. The simulated time for which given ODE is solved can be limited by `tspan`.  If `tspan` is a number, it is equivalent to passing `(zero(tspan), tspan)`.

Example usage:

```julia
using SteadyStateDiffEq, OrdinaryDiffEq
sol = solve(prob, DynamicSS(Tsit5()))

using Sundials
sol = solve(prob, DynamicSS(CVODE_BDF()); dt = 1.0)
```

!!! note
    The default `alg` of `nothing` works only if `DifferentialEquations.jl` is installed and loaded.


!!! note
    If you use `CVODE_BDF` you may need to give a starting `dt` via `dt = ....`.*

