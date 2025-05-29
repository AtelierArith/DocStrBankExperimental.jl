```
jacobian(ds::CoreDynamicalSystem)
```

Construct the Jacobian rule for the dynamical system `ds`. If the system already has a Jacobian rule constructed via ModelingToolkit.jl it returns this, otherwise it constructs the Jacobian rule with automatic differentiation using module [`ForwardDiff`](https://github.com/JuliaDiff/ForwardDiff.jl).

## Description

For out-of-place systems, `jacobian` returns the Jacobian rule as a function `Jf(u, p, t = 0) -> J0::SMatrix`. Calling `Jf(u, p, t)` will compute the Jacobian at the state `u`, parameters `p` and time `t` and return the result as `J0`. For in-place systems, `jacobian` returns the Jacobian rule as a function `Jf!(J0, u, p, t = 0)`. Calling `Jf!(J0, u, p)` will compute the Jacobian at the state `u`, parameters `p` and time `t` and save the result in `J0`.
