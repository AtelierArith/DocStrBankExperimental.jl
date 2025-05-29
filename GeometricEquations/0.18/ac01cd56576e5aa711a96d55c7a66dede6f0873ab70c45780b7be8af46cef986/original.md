`HODEEnsemble`: Hamiltonian Ordinary Differential Equation Ensemble

A canonical Hamiltonian system of equations is special case of a partitioned ordinary differential equation,

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t), p(t)) , \\
\dot{p} (t) &= f(t, q(t), p(t)) ,
\end{aligned}
$$

with vector fields $v$ and $f$, given by

$$
\begin{aligned}
v &=   \frac{\partial H}{\partial p} , &
f &= - \frac{\partial H}{\partial q} .
\end{aligned}
$$

The dynamical variables $(q,p)$ take values in $T^{*} Q \simeq \mathbb{R}^{d} \times \mathbb{R}^{d}$.

### Constructors

```julia
HODEEnsemble(v, f, hamiltonian, tspan, tstep, ics::AbstractVector{<: NamedTuple}; kwargs...)
HODEEnsemble(v, f, hamiltonian, tspan, tstep, q₀::AbstractVector{<: StateVariable}, p₀::AbstractVector{<: StateVariable}; kwargs...)
HODEEnsemble(v, f, hamiltonian, tspan, tstep, q₀::AbstractVector{<: AbstractArray}, p₀::AbstractVector{<: AbstractArray}; kwargs...)
```

where `v` and `f` are the function computing the vector fields,  `hamiltonian` returns the value of the Hamiltonian (i.e. the total energy), `tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is an `AbstractVector` of `NamedTuple`, each with entries `q` and `p`. The initial conditions `q₀` and `p₀` can also be prescribed, each as an `AbstractVector` of `StateVariable` or `AbstractArray{<:Number}`. For the interfaces of the functions `v`, `f` and `hamiltonian` see [`HODE`](@ref).

For possible keyword arguments see the documentation on [`EnsembleProblem`](@ref GeometricEquations.EnsembleProblem) subtypes.
