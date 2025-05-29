`SODEProblem`: Split Ordinary Differential Equation Problem

Defines an initial value problem

$$
\dot{q} (t) = v(t, q(t)) , \qquad q(t_{0}) = q_{0} ,
$$

with vector field $v$, initial condition $q_{0}$ and the solution $q$ taking values in $\mathbb{R}^{d}$. Here, the vector field $v$ is given as a sum of vector fields

$$
v (t) = v_1 (t) + ... + v_r (t) .
$$

The dynamical variables $q$ with initial condition $q_{0}$ take values in $\mathbb{R}^{d}$.

### Constructors

```julia
SODEProblem(v, q, tspan, tstep, ics::NamedTuple; kwargs...)
SODEProblem(v, q, tspan, tstep, q₀::StateVariable; kwargs...)
SODEProblem(v, q, tspan, tstep, q₀::AbstractArray; kwargs...)
SODEProblem(v, tspan, tstep, ics::NamedTuple; kwargs...)
SODEProblem(v, tspan, tstep, q₀::StateVariable; kwargs...)
SODEProblem(v, tspan, tstep, q₀::AbstractArray; kwargs...)
```

where `v` is a tuple of functions computing the vector fields for each substep,  `q` is an optional tuple of functions computing the solution for each substep, `tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is a `NamedTuple` with entry `q`. The initial condition `q₀` can also be prescribed directly, with `StateVariable` an `AbstractArray{<:Number}`.

For possible keyword arguments see the documentation on [`EquationProblem`](@ref GeometricEquations.EquationProblem) subtypes.

### Function Definitions

The functions `v_i` providing the vector field must have the interface

```julia
function v_i(v, t, q, params)
    v[1] = ...
    v[2] = ...
    ...
end
```

and the functions `q_i` providing the solutions must have the interface

```julia
function q_i(q₁, t₁, q₀, t₀, params)
    q₁[1] = q₀[1] + ...
    q₁[2] = q₀[2] + ...
    ...
end
```

where `t₀` is the current time, `q₀` is the current solution vector, `q₁` is the new solution vector at time `t₁`, holding the result of computing one substep

The fact that the function `v` returns the solution and not just the vector field for each substep increases the flexibility for the use of splitting methods, e.g., it allows to use another integrator for solving substeps. with the vector field $v_i$.
