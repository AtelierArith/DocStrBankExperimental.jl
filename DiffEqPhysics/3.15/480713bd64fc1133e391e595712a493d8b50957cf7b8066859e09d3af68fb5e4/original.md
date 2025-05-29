```
HamiltonianProblem(H, p0, q0, tspan, param=nothing; kwargs...)
HamiltonianProblem((dp, dq), p0, q0, tspan, param=nothing; kwargs...)
```

Define a physical system by its Hamiltonian function `H(p, q, param)` or the function pair `dp = -∂H/∂q` and `dq = ∂H/∂p`.

The equations of motion are then given by `q̇ = ∂H/∂p = dq` and `ṗ  = -∂H/∂q = dp`.

The initial values for canonical impulses `p0` and coordinates `q0` may be scalars, `SArray`s or other `AbstractArray`s. Their type determines the type of functions `dp` and `dq`.

In the first two cases the derivative functions require the signatures `dp(p, q, param, t)` and `dq(p, q, param, t)` while in the latter case the partial derivatives use mutating signatures `dp!(Δp, p, q, param, t)` and `dq!(Δq, p, q, param, t)` with predefined arrays `Δp` and `Δq`.

If the Hamiltonian function is given, `dp` and `dq` are calculated automatically using AD (`ForwardDiff`).

!!! note



`H` may be defined with or without time as fourth argument. If both methods are defined, that with 4 arguments is used.
