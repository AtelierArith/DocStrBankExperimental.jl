`LODEProblem`: Lagrangian Ordinary Differential Equation Problem

A Lagrangian system of equations is a special case of an implicit ordinary differential equations, that is an implicit initial value problem of the form

$$
\begin{aligned}
\dot{q} (t) &= v(t) , \\
\dot{p} (t) &= f(t, q(t), v(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) ,
\end{aligned}
$$

with momentum $p$ and force field $f$, given by

$$
\begin{aligned}
p &= \frac{\partial L}{\partial v} , &
f &= \frac{\partial L}{\partial q} .
\end{aligned}
$$

This is a special case of an implicit ordinary differential equation, that is defined by a Lagrangian, as well as a special case of a differential algebraic equation with dynamical variables $(q,p)$ and algebraic variable $v$, that is determined such that the constraint $p(t) = ϑ(t, q(t), v(t))$ is satisfied.

Many integrators perform a projection step in order to enforce this constraint. To this end, the system is extended to

$$
\begin{aligned}
\dot{q} (t) &= v(t) + \lambda(t) , \\
\dot{p} (t) &= f(t, q(t), v(t)) + g(t, q(t), v(t), \lambda(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) ,
\end{aligned}
$$

where the vector field defining the projection step is usually given as

$$
\begin{aligned}
g(t, q(t), v(t), λ(t)) &= λ(t) \cdot \nabla ϑ(t, q(t), v(t)) .
\end{aligned}
$$

The dynamical variables $(q,p)$ with initial conditions $(q(t_{0}) = q_{0}, p(t_{0}) = p_{0})$ take values in $T^{*} Q \simeq \mathbb{R}^{d} \times \mathbb{R}^{d}$. The algebraic variable $λ$ with initial condition $λ(t_{0}) = λ_{0}$ takes values in $\mathbb{R}^{m}$.

### Constructors

```julia
LODEProblem(ϑ, f, ω, l, tspan, tstep, ics; kwargs...)
LODEProblem(ϑ, f, ω, l, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::AlgebraicVariable; kwargs...)
LODEProblem(ϑ, f, ω, l, tspan, tstep, q₀::AbstractArray, p₀::AbstractArray, λ₀::AbstractArray = zero(q₀); kwargs...)
LODEProblem(ϑ, f, g, ω, l, tspan, tstep, ics; kwargs...)
LODEProblem(ϑ, f, g, ω, l, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::AlgebraicVariable; kwargs...)
LODEProblem(ϑ, f, g, ω, l, tspan, tstep, q₀::AbstractArray, p₀::AbstractArray, λ₀::AbstractArray = zero(q₀); kwargs...)
```

where `ϑ`, `f` and `g` are the functions computing the momentum and the vector fields, respectively, `ω` determines the symplectic matrix, and `l` returns the Lagrangian, `tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is a `NamedTuple` with entries `q`, `p` and `λ`. The initial conditions `q₀`, `p₀` and `λ₀` can also be prescribed directly, with `StateVariable` an `AbstractArray{<:Number}`, where `λ₀` can also be omitted. For the interfaces of the functions `ϑ`, `f`, `g`, `ω` and `l` see [`LODE`](@ref).

In addition to the standard keyword arguments for [`EquationProblem`](@ref GeometricEquations.EquationProblem) subtypes, a `LODEProblem` accepts functions `v̄` and `f̄` for the computation of initial guesses for the vector fields with default values `v̄ = _lode_default_v̄` and `f̄ = f`.
