`IODE`: Implicit Ordinary Differential Equation

An implicit ordinary differential equations is an initial value problem of the form

$$
\begin{aligned}
\dot{q} (t) &= v(t) , \\
\dot{p} (t) &= f(t, q(t), v(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) ,
\end{aligned}
$$

with force field $f$, the momentum defined by $p$. This is a special case of a differential algebraic equation with dynamical variables $(q,p)$ and algebraic variable $v$, that is determined such that the constraint $p(t) = ϑ(t, q(t), v(t))$ is satisfied.

Many integrators perform a projection step in order to enforce this constraint. To this end, the system is extended to

$$
\begin{aligned}
\dot{q} (t) &= v(t) + λ(t) , \\
\dot{p} (t) &= f(t, q(t), v(t)) + g(t, q(t), v(t), λ(t)) , \\
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

  * `ϑType <: Callable`: type of `ϑ`
  * `fType <: Callable`: type of `f`
  * `gType <: Callable`: type of `g`
  * `v̄Type <: Callable`: type of `v̄`
  * `f̄Type <: Callable`: type of `f̄`
  * `invType <: OptionalInvariants`: invariants type
  * `parType <: OptionalParameters`: parameters type
  * `perType <: OptionalPeriodicity`: periodicity type

### Fields

  * `ϑ`: function determining the momentum
  * `f`: function computing the vector field
  * `g`: function determining the projection, given by $\nabla \vartheta (t,q,v) \cdot \lambda$
  * `v̄`: function computing an initial guess for the velocity field $v$ (optional)
  * `f̄`: function computing an initial guess for the force field $f$ (optional)
  * `invariants`: functions for the computation of invariants, either a `NamedTuple` containing the equation's invariants or `NullInvariants`
  * `parameters`: type constraints for parameters, either a `NamedTuple` containing the equation's parameters or `NullParameters`
  * `periodicity`: determines the periodicity of the state vector `q` for cutting periodic solutions, either a `AbstractArray` or `NullPeriodicity`

### Constructors

```julia
IODE(ϑ, f, g, v̄, f̄, invariants, parameters, periodicity)
IODE(ϑ, f, g; v̄ = _iode_default_v̄, f̄ = f, invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

where 

```julia
_iode_default_v̄(v, t, q, params) = nothing
```

The functions `ϑ`, `f` and `g` compute the momentum and the vector fields, respectively.

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

where `t` is the current time, `q` is the current solution vector, `v` is the current velocity and `f` and `p` are the vectors which hold the result of evaluating the functions $f$ and $ϑ$ on `t`, `q` and `v`. In addition, the functions `g`, `v̄` and `f̄` are specified by

```julia
function g(g, t, q, v, λ)
    g[1] = ...
    g[2] = ...
    ...
end

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

The function `g` is used in projection methods that enforce $p = ϑ(q)$. The functions `v̄` and `f̄` are used for initial guesses in nonlinear implicit solvers.
