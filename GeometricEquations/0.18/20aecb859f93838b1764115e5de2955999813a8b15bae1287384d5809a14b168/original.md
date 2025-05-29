`DELEEnsemble`: Discrete Euler-Lagrange Equation Ensemble

Discrete Euler-Lagrange equations define an initial value problem of the form

$$
D_1 L_d (q_{n}, q_{n+1}) + D_2 L_d (q_{n-1}, q_{n}) = 0 ,
$$

with discrete Lagrangian $L_d$.

The dynamical variables $q$ take values in $\mathbb{R}^{d}$.

### Constructors

```julia
DELEEnsemble(Ld, D1Ld, D2Ld, tspan, tstep, ics::AbstractVector{<: NamedTuple}; kwargs...)
DELEEnsemble(Ld, D1Ld, D2Ld, tspan, tstep, q₀::AbstractVector{<: StateVariable}, q₁::AbstractVector{<: StateVariable}; kwargs...)
DELEEnsemble(Ld, D1Ld, D2Ld, tspan, tstep, q₀::AbstractVector{<: AbstractArray}, q₁::AbstractVector{<: AbstractArray}; kwargs...)
```

where `Ld` is the function computing the discrete Lagrangian, `D1Ld` and `D2Ld` are functions computing the derivative of `Ld` with respect to the first and second argument, `tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is an `AbstractVector` of `NamedTuple`, each with entries `q₀` and  `q₁` of type `StateVariable`. The initial conditions `q₀` and  `q₁` can also be prescribed as two `AbstractVector`s of `StateVariable` or `AbstractArray{<:Number}`. For the interface of the functions `Ld`, `D1Ld` and `D2Ld` see [`DELE`](@ref).

For possible keyword arguments see the documentation on [`EnsembleProblem`](@ref GeometricEquations.EnsembleProblem) subtypes.
