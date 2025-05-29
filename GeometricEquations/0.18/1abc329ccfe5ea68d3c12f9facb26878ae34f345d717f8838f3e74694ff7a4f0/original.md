`SDE`: Stratonovich Stochastic Differential Equation

Defines a stochastic differential initial value problem

$$
\begin{aligned}
dq (t) &= v(t, q(t)) \, dt + B(t, q(t)) \circ dW , & q(t_{0}) &= q_{0} ,
\end{aligned}
$$

with drift vector field $v$, diffusion matrix $B$, initial conditions $q_{0}$, the dynamical variable $q$ taking values in $\mathbb{R}^{d}$, and the m-dimensional Wiener process W

### Parameters

  * `vType <: Callable`: type of `v`
  * `BType <: Callable`: type of `B`
  * `invType <: OptionalInvariants`: invariants type
  * `parType <: OptionalParameters`: parameters type
  * `perType <: OptionalPeriodicity`: periodicity type

### Fields

  * `v`:  function computing the deterministic vector field
  * `B`:  function computing the d x m diffusion matrix
  * `invariants`: functions for the computation of invariants, either a `NamedTuple` containing the equation's invariants or `NullInvariants`
  * `parameters`: type constraints for parameters, either a `NamedTuple` containing the equation's parameters or `NullParameters`
  * `periodicity`: determines the periodicity of the state vector `q` for cutting periodic solutions, either a `AbstractArray` or `NullPeriodicity`

### Constructors

```julia
SDE(v, B, invariants, parameters, periodicity)
SDE(v, B; invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

The functions `v` and `B`, providing the drift vector field and diffusion matrix. The function `v` must have the interface

```julia
function v(v, t, q, params)
    v[1] = ...
    v[2] = ...
    ...
end
```

where `t` is the current time, `q` is the current solution vector, `v` is the vector which holds the result of evaluating the vector field $v$ on `t` and `q`, and params are additional parameters. The function `B` should have a method with interface

```julia
function B(B, t, q, params)
    B[1,1] = ...
    ...
end
```
