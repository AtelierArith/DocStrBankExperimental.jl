`ODEProblem`: Ordinary Differential Equation Problem

Ordinary differential equations define an initial value problem of the form

$$
\dot{q} (t) = v(t, q(t)) ,
$$

with vector field $v$.

The dynamical variables $q$ with initial condition $q_{0}$ take values in $\mathbb{R}^{d}$.

### Constructors

```julia
ODEProblem(v, tspan, tstep, ics::NamedTuple; kwargs...)
ODEProblem(v, tspan, tstep, q₀::StateVariable; kwargs...)
ODEProblem(v, tspan, tstep, q₀::AbstractArray; kwargs...)
```

where `v` is the function computing the vector field,  `tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is a `NamedTuple` with entry `q` of type `StateVariable`. The initial condition `q₀` can also be prescribed directly, as a `StateVariable` or an `AbstractArray{<:Number}`.

For possible keyword arguments see the documentation on [`EquationProblem`](@ref GeometricEquations.EquationProblem) subtypes.

### Function Definitions

The function `v` providing the vector field must have the interface

```julia
function v(v, t, q, params)
    v[1] = ...
    v[2] = ...
    ...
end
```

where `t` is the current time, `q` is the current solution vector, `v` is the vector which holds the result of evaluating the vector field $v$ on `t` and `q`, and `params` is a `NamedTuple` of additional parameters on which the vector field may depend.
