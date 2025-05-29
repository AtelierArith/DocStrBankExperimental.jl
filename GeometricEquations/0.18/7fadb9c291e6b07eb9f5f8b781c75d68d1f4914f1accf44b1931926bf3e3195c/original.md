`ODE`: Ordinary Differential Equation

Ordinary differential equations define an initial value problem of the form

$$
\dot{q} (t) = v(t, q(t)) ,
$$

with vector field $v$.

### Parameters

  * `vType <: Callable`: type of `v`
  * `invType <: OptionalInvariants`: invariants type
  * `parType <: OptionalParameters`: parameters type
  * `perType <: OptionalPeriodicity`: periodicity type

### Fields

  * `v`: function computing the vector field
  * `invariants`: functions for the computation of invariants, either a `NamedTuple` containing the equation's invariants or `NullInvariants`
  * `parameters`: type constraints for parameters, either a `NamedTuple` containing the equation's parameters or `NullParameters`
  * `periodicity`: determines the periodicity of the state vector `q` for cutting periodic solutions, either a `AbstractArray` or `NullPeriodicity`

### Constructors

```julia
ODE(v, invariants, parameters, periodicity)
ODE(v; invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

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
