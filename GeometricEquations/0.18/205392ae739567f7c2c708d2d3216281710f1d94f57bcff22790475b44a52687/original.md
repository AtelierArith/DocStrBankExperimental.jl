`IODEEnsemble`: Implicit Ordinary Differential Equation Ensemble

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

The dynamical variables $(q,p)$ take values in $\mathbb{R}^{d} \times \mathbb{R}^{d}$. The algebraic variable $λ$ takes values in $\mathbb{R}^{m}$.

### Constructors

```julia
IODEEnsemble(ϑ, f, tspan, tstep, ics::AbstractVector{<: NamedTuple}; kwargs...)
IODEEnsemble(ϑ, f, tspan, tstep, q₀::AbstractVector{<: StateVariable}, p₀::AbstractVector{<: StateVariable}, λ₀::AbstractVector{<: AlgebraicVariable}; kwargs...)
IODEEnsemble(ϑ, f, tspan, tstep, q₀::AbstractVector{<: AbstractArray}, p₀::AbstractVector{<: AbstractArray}, λ₀::AbstractVector{<: AbstractArray}; kwargs...)
IODEEnsemble(ϑ, f, g, tspan, tstep, ics::AbstractVector{<: NamedTuple}; kwargs...)
IODEEnsemble(ϑ, f, g, tspan, tstep, q₀::AbstractVector{<: StateVariable}, p₀::AbstractVector{<: StateVariable}, λ₀::AbstractVector{<: AlgebraicVariable}; kwargs...)
IODEEnsemble(ϑ, f, g, tspan, tstep, q₀::AbstractVector{<: AbstractArray}, p₀::AbstractVector{<: AbstractArray}, λ₀::AbstractVector{<: AbstractArray}; kwargs...)
```

The functions `ϑ`, `f` and `g` compute the momentum and the vector fields, respectively.

`tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is a `NamedTuple` with entries `q`, `p` and `λ`. `ics` is an `AbstractVector` of `NamedTuple`, each with entries `q`, `p` and `λ`. The initial conditions `q₀`, `p₀` and `λ₀` can also be prescribed, each as an `AbstractVector` of `StateVariable` or `AbstractArray{<:Number}`. For the interfaces of the functions `ϑ`, `f` and `g` see [`IODE`](@ref).

In addition to the standard keyword arguments for [`EquationProblem`](@ref GeometricEquations.EquationProblem) subtypes, an `IODEEnsemble` accepts functions `v̄` and `f̄` for the computation of initial guesses for the vector fields with default values `v̄ = _iode_default_v̄` and `f̄ = f`.

For possible keyword arguments see the documentation on [`EnsembleProblem`](@ref GeometricEquations.EnsembleProblem) subtypes.
