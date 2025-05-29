`IODEProblem`: Implicit Ordinary Differential Equation Problem

An implicit ordinary differential equations is an initial value problem of the form

$$
\begin{aligned}
\dot{q} (t) &= v(t) , \\
\dot{p} (t) &= f(t, q(t), v(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) ,
\end{aligned}
$$

with force field $f$, the momentum defined by $p$. This is a special case of a differential algebraic equation with dynamical variables $(q,p)$ and algebraic variable $v$, that is determined such that the constraint $p(t) = ϑ(t, q(t), v(t))$ is satisfied.

Many integrators perform a projection step in order to enforce this constraint. To this end, the system is extended to

$$
\begin{aligned}
\dot{q} (t) &= v(t) + λ(t) , \\
\dot{p} (t) &= f(t, q(t), v(t)) + g(t, q(t), v(t), λ(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) ,
\end{aligned}
$$

where the vector field defining the projection step is usually given as

$$
\begin{aligned}
g(t, q(t), v(t), λ(t)) &= λ(t) \cdot \nabla ϑ(t, q(t), v(t)) .
\end{aligned}
$$

The dynamical variables $(q,p)$ with initial conditions $(q(t_{0}) = q_{0}, p(t_{0}) = p_{0})$ take values in $\mathbb{R}^{d} \times \mathbb{R}^{d}$. The algebraic variable $v$ with initial condition $v(t_{0}) = v_{0}$ takes values in $\mathbb{R}^{d}$.

### Constructors

```julia
IODEProblem(ϑ, f, tspan, tstep, ics; kwargs...)
IODEProblem(ϑ, f, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::AlgebraicVariable; kwargs...)
IODEProblem(ϑ, f, tspan, tstep, q₀::AbstractArray, p₀::AbstractArray, λ₀::AbstractArray = zero(q₀); kwargs...)
IODEProblem(ϑ, f, g, tspan, tstep, ics; kwargs...)
IODEProblem(ϑ, f, g, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::AlgebraicVariable; kwargs...)
IODEProblem(ϑ, f, g, tspan, tstep, q₀::AbstractArray, p₀::AbstractArray, λ₀::AbstractArray = zero(q₀); kwargs...)
```

The functions `ϑ`, `f` and `g` compute the momentum and the vector fields, respectively.

`tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is a `NamedTuple` with entries `q`, `p` and `λ`. The initial conditions `q₀` and `p₀` can also be prescribed directly, with `StateVariable` an `AbstractArray{<:Number}`. For the interfaces of the functions `ϑ`, `f` and `g` see [`IODE`](@ref).

In addition to the standard keyword arguments for [`EquationProblem`](@ref GeometricEquations.EquationProblem) subtypes, an `IODEProblem` accepts functions `v̄` and `f̄` for the computation of initial guesses for the vector fields with default values `v̄ = _iode_default_v̄` and `f̄ = f`.

Initial conditions have to be prescribed for `(q,p)`. If instead initial conditions are available only for `(q,v)`, the function `ϑ` can be called to compute the corresponding initial value of `p`.
