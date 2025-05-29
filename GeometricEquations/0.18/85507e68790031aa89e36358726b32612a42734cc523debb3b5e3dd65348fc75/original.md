`HODE`: Hamiltonian Ordinary Differential Equation

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

### Parameters

  * `vType <: Callable`: type of `v`
  * `fType <: Callable`: type of `f`
  * `hamType <: Callable`: Hamiltonian type
  * `invType <: OptionalInvariants`: invariants type
  * `parType <: OptionalParameters`: parameters type
  * `perType <: OptionalPeriodicity`: periodicity type

### Fields

  * `v`: function computing the vector field $v$
  * `f`: function computing the vector field $f$
  * `hamiltonian`: function computing the Hamiltonian $H$ (usually the total energy of the system)
  * `invariants`: functions for the computation of invariants, either a `NamedTuple` containing the equation's invariants or `NullInvariants`
  * `parameters`: type constraints for parameters, either a `NamedTuple` containing the equation's parameters or `NullParameters`
  * `periodicity`: determines the periodicity of the state vector `q` for cutting periodic solutions, either a `AbstractArray` or `NullPeriodicity`

### Constructors

```julia
HODE(v, f, hamiltonian, invariants, parameters, periodicity)
HODE(v, f, hamiltonian; invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

### Function Definitions

The functions `v`, `f` and `hamiltonian` must have the interface

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

function hamiltonian(t, q, p, params)
    return ...
end
```

where `t` is the current time, `q` and `p` are the current solution vectors, `v` and `f` are the vectors which hold the result of evaluating the vector fields on `t`, `q` and `p`, and params is a `NamedTuple` of additional parameters.
