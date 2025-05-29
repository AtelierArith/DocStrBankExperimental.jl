`LODE`: Lagrangian Ordinary Differential Equation

A Lagrangian system of equations is a special case of an implicit ordinary differential equations, that is an implicit initial value problem of the form

$$
\begin{aligned}
\dot{q} (t) &= v(t) , \\
\dot{p} (t) &= f(t, q(t), v(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) ,
\end{aligned}
$$

with momentum $p$ and force field $f$, given by

$$
\begin{aligned}
p &= \frac{\partial L}{\partial v} , &
f &= \frac{\partial L}{\partial q} .
\end{aligned}
$$

This is a special case of an implicit ordinary differential equation, that is defined by a Lagrangian, as well as a special case of a differential algebraic equation with dynamical variables $(q,p)$ and algebraic variable $v$, that is determined such that the constraint $p(t) = ϑ(t, q(t), v(t))$ is satisfied.

Many integrators perform a projection step in order to enforce this constraint. To this end, the system is extended to

$$
\begin{aligned}
\dot{q} (t) &= v(t) + \lambda(t) , \\
\dot{p} (t) &= f(t, q(t), v(t)) + g(t, q(t), v(t), \lambda(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) ,
\end{aligned}
$$

where the vector field defining the projection step is usually given as

$$
\begin{aligned}
g(t, q(t), v(t), λ(t)) &= λ(t) \cdot \nabla ϑ(t, q(t), v(t)) .
\end{aligned}
$$

### Parameters

  * `ϑType <: Function`: type of `ϑ`
  * `fType <: Function`: type of `f`
  * `gType <: Function`: type of `g`
  * `ωType <: Function`: type of `ω`
  * `v̄Type <: Function`: type of `v̄`
  * `f̄Type <: Function`: type of `f̄`
  * `lagType <: Function`: Lagrangian type
  * `invType <: OptionalInvariants`: invariants type
  * `parType <: OptionalParameters`: parameters type
  * `perType <: OptionalPeriodicity`: periodicity type

### Fields

  * `ϑ`: function determining the momentum
  * `f`: function computing the vector field
  * `g`: function determining the projection, given by $\nabla \vartheta (q) \cdot \lambda$
  * `ω`: function computing the symplectic matrix
  * `v̄`: function computing an initial guess for the velocity field $v$ (optional)
  * `f̄`: function computing an initial guess for the force field $f$ (optional)
  * `lagrangian`: function computing the Lagrangian $L$
  * `invariants`: functions for the computation of invariants, either a `NamedTuple` containing the equation's invariants or `NullInvariants`
  * `parameters`: type constraints for parameters, either a `NamedTuple` containing the equation's parameters or `NullParameters`
  * `periodicity`: determines the periodicity of the state vector `q` for cutting periodic solutions, either a `AbstractArray` or `NullPeriodicity`

### Constructors

```julia
LODE(ϑ, f, g, ω, l, v̄, f̄, invariants, parameters, periodicity)
LODE(ϑ, f, g, ω, l; v̄ = _lode_default_v̄, f̄ = f, invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

where 

```julia
_lode_default_v̄(v, t, q, params) = nothing
```

### Function Definitions

The functions `ϑ` and `f` must have the interface

```julia
function ϑ(p, t, q, v)
    p[1] = ...
    p[2] = ...
    ...
end
```

and

```julia
function f(f, t, q, v)
    f[1] = ...
    f[2] = ...
    ...
end
```

where `t` is the current time, `q` is the current solution vector, `v` is the current velocity and `f` and `p` are the vectors which hold the result of evaluating the functions $f$ and $ϑ$ on `t`, `q` and `v`. The funtions `g`, `v̄` and `f̄` are specified by

```julia
function g(g, t, q, λ)
    g[1] = ...
    g[2] = ...
    ...
end
```

and

```julia
function v̄(v, t, q, p)
    v[1] = ...
    v[2] = ...
    ...
end

function f̄(f, t, q, v)
    f[1] = ...
    f[2] = ...
    ...
end
```

The function `g` is used in projection methods that enforce $p = ϑ(q)$. The functions `v̄` and `f̄` are used for initial guesses in nonlinear implicit solvers. Finally, the functions `ω` and `l`, computing the symplectic matrix and the Lagrangian, have the following signature

```julia
function ω(f, t, q, v, params)
    ω[1,1] = ...
    ω[1,2] = ...
    ...
end

function l(t, q, v, params)
    return ...
end
```
