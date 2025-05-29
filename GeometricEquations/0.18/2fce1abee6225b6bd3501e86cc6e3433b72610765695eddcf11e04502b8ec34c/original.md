`DELE`: Discrete Euler-Lagrange Equation

Discrete Euler-Lagrange equations define an initial value problem of the form

$$
D_1 L_d (q_{n}, q_{n+1}) + D_2 L_d (q_{n-1}, q_{n}) = 0 ,
$$

with discrete Lagrangian $L_d$.

### Parameters

  * `LdType <: Callable`: type of `Ld`
  * `D1LdType <: Callable`: type of `D1Ld`
  * `D2LdType <: Callable`: type of `D2Ld`
  * `invType <: OptionalInvariants`: invariants type
  * `parType <: OptionalParameters`: parameters type
  * `perType <: OptionalPeriodicity`: periodicity type

### Fields

  * `Ld`: function computing the discrete Lagrangian
  * `D1Ld`: function computing the derivative of the discrete Lagrangian w.r.t. the first argument
  * `D2Ld`: function computing the derivative of the discrete Lagrangian w.r.t. the second argument
  * `invariants`: functions for the computation of invariants, either a `NamedTuple` containing the equation's invariants or `NullInvariants`
  * `parameters`: type constraints for parameters, either a `NamedTuple` containing the equation's parameters or `NullParameters`
  * `periodicity`: determines the periodicity of the state vector `q` for cutting periodic solutions, either a `AbstractArray` or `NullPeriodicity`

### Constructors

```julia
DELE(Ld, D1Ld, D2Ld, invariants, parameters, periodicity)
DELE(Ld, D1Ld, D2Ld; invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

### Function Definitions

The function `Ld` providing the discrete Lagrangian must have the interface

```julia
function Ld(t_{n}, t_{n+1}, q_{n}, q_{n+1}, params)
    return ...
end
```

where `t_{n}` and `t_{n+1}` are the time of the previous and next step, `q_{n}` and `q_{n+1}` are the solution vectors of the previous and next step, and `params` is a `NamedTuple` of additional parameters on which the Lagrangian may depend. The derivatives of the discrete Lagrangian with respect to its first and second argument, `D_1 L_d` and `D_2 L_d`, respectively, must have the interfaces

```julia
function D1Ld(D, t_{n}, t_{n+1}, q_{n}, q_{n+1}, params)
    D1[1] = ...
    D1[2] = ...
    ...
end
```

and

```julia
function D2Ld(D2, t_{n}, t_{n+1}, q_{n}, q_{n+1}, params)
    D2[1] = ...
    D2[2] = ...
    ...
end
```
