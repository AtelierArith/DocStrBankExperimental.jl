`SODEEnsemble`: Split Ordinary Differential Equation Ensemble

Defines an initial value problem

$$
\dot{q} (t) = v(t, q(t)) , \qquad q(t_{0}) = q_{0} ,
$$

with vector field $v$, initial condition $q_{0}$ and the solution $q$ taking values in $\mathbb{R}^{d}$. Here, the vector field $v$ is given as a sum of vector fields

$$
v (t) = v_1 (t) + ... + v_r (t) .
$$

The dynamical variables $q$ take values in $\mathbb{R}^{d}$.

### Constructors

```julia
SODEEnsemble(v, q, tspan, tstep, ics::AbstractVector{<: NamedTuple}; kwargs...)
SODEEnsemble(v, q, tspan, tstep, q₀::AbstractVector{<: StateVariable}; kwargs...)
SODEEnsemble(v, q, tspan, tstep, q₀::AbstractVector{<: AbstractArray}; kwargs...)
SODEEnsemble(v, tspan, tstep, ics::AbstractVector{<: NamedTuple}; kwargs...)
SODEEnsemble(v, tspan, tstep, q₀::AbstractVector{<: StateVariable}; kwargs...)
SODEEnsemble(v, tspan, tstep, q₀::AbstractVector{<: AbstractArray}; kwargs...)
```

where `v` is a tuple of functions computing the vector fields for each substep,  `q` is an optional tuple of functions computing the solution for each substep, `tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is an `AbstractVector` of `NamedTuple`, each with an entry `q` of type `StateVariable`. The initial condition `q₀` can also be prescribed as an `AbstractVector` of `StateVariable` or `AbstractArray{<:Number}`. For the interface of the functions `v` and `q` see [`SODE`](@ref).

For possible keyword arguments see the documentation on [`EnsembleProblem`](@ref GeometricEquations.EnsembleProblem) subtypes.
