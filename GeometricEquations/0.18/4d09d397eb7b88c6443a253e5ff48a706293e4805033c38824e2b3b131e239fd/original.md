`PODEEnsemble`: Partitioned Ordinary Differential Equation Ensemble

A partitioned ordinary differential equation is an initial value problem of the form

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t), p(t)) , \\
\dot{p} (t) &= f(t, q(t), p(t)) ,
\end{aligned}
$$

with vector fields $v$ and $f$.

The dynamical variables $(q,p)$ take values in $\mathbb{R}^{d} \times \mathbb{R}^{d}$.

### Constructors

```julia
PODEEnsemble(v, f, tspan, tstep, ics::AbstractVector{<: NamedTuple}; kwargs...)
PODEEnsemble(v, f, tspan, tstep, q₀::AbstractVector{<: StateVariable}, p₀::AbstractVector{<: StateVariable}; kwargs...)
PODEEnsemble(v, f, tspan, tstep, q₀::AbstractVector{<: AbstractArray}, p₀::AbstractVector{<: AbstractArray}; kwargs...)
```

where `v` and `f` are the function computing the vector fields,  `tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is an `AbstractVector` of `NamedTuple`, each with entries `q` and `p`. The initial conditions `q₀` and `p₀` can also be prescribed, each as an `AbstractVector` of `StateVariable` or `AbstractArray{<:Number}`. For the interfaces of the functions `v` and `f` see [`PODE`](@ref).

For possible keyword arguments see the documentation on [`EnsembleProblem`](@ref GeometricEquations.EnsembleProblem) subtypes.
