`ODEEnsemble`: Ordinary Differential Equation Ensemble

Ordinary differential equations define an initial value problem of the form

$$
\dot{q} (t) = v(t, q(t)) ,
$$

with vector field $v$.

The dynamical variables $q$ take values in $\mathbb{R}^{d}$.

### Constructors

```julia
ODEEnsemble(v, tspan, tstep, ics::AbstractVector{<: NamedTuple}; kwargs...)
ODEEnsemble(v, tspan, tstep, q₀::AbstractVector{<: StateVariable}; kwargs...)
ODEEnsemble(v, tspan, tstep, q₀::AbstractVector{<: AbstractArray}; kwargs...)
```

where `v` is the function computing the vector field,  `tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and  `ics` is an `AbstractVector` of `NamedTuple`, each with an entry `q` of type `StateVariable`. The initial condition `q₀` can also be prescribed as an `AbstractVector` of `StateVariable` or `AbstractArray{<:Number}`. For the interface of the function `v` see [`ODE`](@ref).

For possible keyword arguments see the documentation on [`EnsembleProblem`](@ref GeometricEquations.EnsembleProblem) subtypes.
