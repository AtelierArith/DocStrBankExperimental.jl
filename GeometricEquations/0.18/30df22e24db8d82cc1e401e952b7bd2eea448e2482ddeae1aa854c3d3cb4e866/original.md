`SDEProblem`: Stratonovich Stochastic Differential Equation Problem

Defines a stochastic differential initial value problem

$$
\begin{aligned}
dq (t) &= v(t, q(t)) \, dt + B(t, q(t)) \circ dW , & q(t_{0}) &= q_{0} ,
\end{aligned}
$$

with drift vector field $v$, diffusion matrix $B$, initial conditions $q_{0}$, the dynamical variable $q$ taking values in $\mathbb{R}^{d}$, and the m-dimensional Wiener process W

### Constructors

```julia
SDEProblem(v, B, tspan, tstep, ics::NamedTuple; kwargs...)
SDEProblem(v, B, tspan, tstep, q₀::StateVariable; kwargs...)
```

where `v` is the function computing the vector field and `B` computes the diffusion matrix `tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is a `NamedTuple` with entry `q`. The initial condition `q₀` can also be prescribed directly, with `StateVariable` an `AbstractArray{<:Number}`.

For possible keyword arguments see the documentation on [`EquationProblem`](@ref GeometricEquations.EquationProblem) subtypes.

### Function Definitions

The functions `v` and `B`, providing the drift vector field and diffusion matrix. The function `v` must have the interface

```julia
function v(v, t, q, params)
    v[1] = ...
    v[2] = ...
    ...
end
```

where `t` is the current time, `q` is the current solution vector, `v` is the vector which holds the result of evaluating the vector field $v$ on `t` and `q`, and params are additional parameters. The function `B` should have a method with interface

```julia
function B(B, t, q, params)
    B[1,1] = ...
    ...
end
```
