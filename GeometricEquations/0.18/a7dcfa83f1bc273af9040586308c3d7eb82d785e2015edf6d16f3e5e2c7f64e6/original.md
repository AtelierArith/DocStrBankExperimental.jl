`IDAEProblem`: Implicit Differential Algebraic Equation Problem

An implicit differential algebraic initial value problem takes the form

$$
\begin{aligned}
\dot{q} (t) &= v(t) + u(t, q(t), v(t), p(t), \lambda(t)) , \\
\dot{p} (t) &= f(t, q(t), v(t)) + g(t, q(t), v(t), p(t), \lambda(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) , \\
0 &= \phi (t, q(t), v(t), p(t)) ,
\end{aligned}
$$

with force field $f$, the momentum defined by $ϑ$, projections $u$ and $g$, algebraic constraint $\phi(t,q,v,p)=0$.

Some integrators also enforce the secondary constraint $\psi$, that is the time derivative of the algebraic constraint $\phi$. In this case, the system of equations is modified as follows

$$
\begin{aligned}
\dot{q} (t) &= v(t) + u(t, q(t), v(t), p(t), \lambda(t)) + \bar{u} (t, q(t), v(t), p(t), \mu(t)) , \\
\dot{p} (t) &= f(t, q(t), v(t)) + g(t, q(t), v(t), p(t), \lambda(t)) + \bar{g} (t, q(t), v(t), p(t), \mu(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) , && \\
0 &= \phi (t, q(t), v(t), p(t)) , \\
0 &= \psi (t, q(t), v(t), p(t), \dot{q} (t), \dot{p} (t)) .
\end{aligned}
$$

The dynamical variables $(q,p)$ with initial conditions $(q(t_{0}) = q_{0}, p(t_{0}) = p_{0})$ take values in $\mathbb{R}^{d} \times \mathbb{R}^{d}$. The algebraic variables $(λ,μ)$ with initial condition $(λ(t_{0}) = λ_{0}, μ(t_{0}) = μ_{0})$ take values in $\mathbb{R}^{m} \times \mathbb{R}^{m}$.

### Constructors

```julia
IDAEProblem(ϑ, f, u, g, ϕ, ū, ḡ, ψ, tspan, tstep, ics; kwargs...)
IDAEProblem(ϑ, f, u, g, ϕ, ū, ḡ, ψ, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::StateVariable = zero(q₀), μ₀::StateVariable = zero(λ₀); kwargs...)
IDAEProblem(ϑ, f, u, g, ϕ, tspan, tstep, ics; kwargs...)
IDAEProblem(ϑ, f, u, g, ϕ, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::StateVariable = zero(q₀); kwargs...)
```

The function `ϑ` computes the momentum, `f` computes the force field, `u` and `g` compute the projections, and `ϕ` provides the algebraic constraint. The functions `ψ`, `ū` and `ḡ` are optional and provide the secondary constraint, that is the time derivative of the algebraic constraint, and the corresponding projection.

`tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is a `NamedTuple` with entries `q` and `p`. The initial conditions `q₀`, `p₀`, `λ₀` and `μ₀` can also be prescribed directly, with `StateVariable` an `AbstractArray{<:Number}`. For the interfaces of the functions `ϑ`, `f`, `u`, `g`, `ϕ`, `ū`, `ḡ`, `ψ` see [`IDAE`](@ref).

In addition to the standard keyword arguments for [`EquationProblem`](@ref GeometricEquations.EquationProblem) subtypes, an `IDAEProblem` accepts functions `v̄` and `f̄` for the computation of initial guesses for the vector fields with default values `v̄ = _idae_default_v̄` and `f̄ = f`.

### Function Definitions

The functions `ϑ` and `f` must have the interface

```julia
function ϑ(p, t, q, v, params)
    p[1] = ...
    p[2] = ...
    ...
end

function f(f, t, q, v, params)
    f[1] = ...
    f[2] = ...
    ...
end
```

where `t` is the current time, `q` is the current solution vector, `v` is the current velocity and `f` and `p` are the vectors which hold the result of evaluating the functions $f$ and $ϑ$ on `t`, `q` and `v`. The funtions `g`, `v̄` and `f̄` are specified by

```julia
function u(u, t, q, v, p, λ, params)
    u[1] = ...
    u[2] = ...
    ...
end

function g(g, t, q, v, p, λ, params)
    g[1] = ...
    g[2] = ...
    ...
end

function v̄(v, t, q, p, params)
    v[1] = ...
    v[2] = ...
    ...
end

function f̄(f, t, q, v, params)
    f[1] = ...
    f[2] = ...
    ...
end
```

Some integrators also enforce the secondary constraint $\psi$ and require the following additional functions

```
function ū(u, t, q, v, p, μ, params)
    u[1] = ...
    u[2] = ...
    ...
end

function ḡ(g, t, q, v, p, μ, params)
    g[1] = ...
    g[2] = ...
    ...
end

function ψ(ψ, t, q, v, p, q̇, ṗ, params)
    ψ[1] = ...
end
```
