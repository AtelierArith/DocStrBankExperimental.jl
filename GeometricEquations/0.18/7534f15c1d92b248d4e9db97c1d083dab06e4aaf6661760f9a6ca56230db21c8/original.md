`PODE`: Partitioned Ordinary Differential Equation

A partitioned ordinary differential equation is an initial value problem of the form

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t), p(t)) , \\
\dot{p} (t) &= f(t, q(t), p(t)) ,
\end{aligned}
$$

with vector fields $v$ and $f$.

### Parameters

  * `vType <: Callable`: type of `v`
  * `fType <: Callable`: type of `f`
  * `invType <: OptionalInvariants`: invariants type
  * `parType <: OptionalParameters`: parameters type
  * `perType <: OptionalPeriodicity`: periodicity type

### Fields

  * `v`: function computing the vector field $v$
  * `f`: function computing the vector field $f$
  * `invariants`: functions for the computation of invariants, either a `NamedTuple` containing the equation's invariants or `NullInvariants`
  * `parameters`: type constraints for parameters, either a `NamedTuple` containing the equation's parameters or `NullParameters`
  * `periodicity`: determines the periodicity of the state vector `q` for cutting periodic solutions, either a `AbstractArray` or `NullPeriodicity`

### Constructors

```julia
PODE(v, f, invariants, parameters, periodicity)
PODE(v, f; invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

### Function Definitions

The functions `v` and `f` must have the interface

```julia
function v(v, t, q, p, params)
    v[1] = ...
    v[2] = ...
    ...
end

function f(f, t, q, p, params)
    f[1] = ...
    f[2] = ...
    ...
end
```

where `t` is the current time, `q` and `p` are the current solution vectors, `v` and `f` are the vectors which hold the result of evaluating the vector fields $v$ and $f$ on `t`, `q` and `p`, and params is a `NamedTuple` of additional parameters.
