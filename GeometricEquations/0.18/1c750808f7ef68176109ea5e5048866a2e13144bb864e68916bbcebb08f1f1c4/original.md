`SODE`: Split Ordinary Differential Equation

Defines an initial value problem

$$
\dot{q} (t) = v(t, q(t)) , \qquad q(t_{0}) = q_{0} ,
$$

with vector field $v$, initial condition $q_{0}$ and the solution $q$ taking values in $\mathbb{R}^{d}$. Here, the vector field $v$ is given as a sum of vector fields

$$
v (t) = v_1 (t) + ... + v_r (t) .
$$

The dynamical variables $q$ with initial condition $q_{0}$ take values in $\mathbb{R}^{d}$.

### Parameters

  * `vType <: Union{Tuple,Nothing}`: type of `v`
  * `qType <: Union{Tuple,Nothing}`: type of `q`
  * `invType <: OptionalInvariants`: invariants type
  * `parType <: OptionalParameters`: parameters type
  * `perType <: OptionalPeriodicity`: periodicity type

### Fields

  * `v`: tuple of functions computing the vector fields for each substep
  * `q`: tuple of functions computing the solutions for each substep
  * `invariants`: functions for the computation of invariants, either a `NamedTuple` containing the equation's invariants or `NullInvariants`
  * `parameters`: type constraints for parameters, either a `NamedTuple` containing the equation's parameters or `NullParameters`
  * `periodicity`: determines the periodicity of the state vector `q` for cutting periodic solutions, either a `AbstractArray` or `NullPeriodicity`

### Constructors

```julia
SODE(v, invariants, parameters, periodicity)
SODE(v; invariants=NullInvariants(), parameters=NullParameters(), periodicity=NullPeriodicity())
SODE(v, q, invariants, parameters, periodicity)
SODE(v, q; invariants=NullInvariants(), parameters=NullParameters(), periodicity=NullPeriodicity())
```

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
