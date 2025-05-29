`LDAE`: Lagrangian Differential Algebraic Equation

A special case of an implicit initial value problem is a Lagrangian differential algebraic equation of the form

$$
\begin{aligned}
\dot{q} (t) &= v(t) + u(t, q(t), v(t), p(t), \lambda(t)) + \bar{u} (t, q(t), v(t), p(t), \mu(t)) , \\
\dot{p} (t) &= f(t, q(t), v(t)) + g(t, q(t), v(t), p(t), \lambda(t)) + \bar{g} (t, q(t), v(t), p(t), \mu(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) , \\
0 &= \phi (t, q(t), v(t), p(t)) , \\
0 &= \psi (t, q(t), v(t), p(t), \dot{q}(t), \dot{p}(t)) ,
\end{aligned}
$$

with momentum $p$ and force field $f$, given by

$$
\begin{aligned}
p &= \frac{\partial L}{\partial v} (q,v) , &
f &= \frac{\partial L}{\partial q} (q,v) ,
\end{aligned}
$$

projection fields $u$, $\bar{u}$ and $g$, $\bar{g}$. This is a special case of a differential algebraic equation with dynamical variables $(q,p)$ and algebraic variables $v$, $\lambda$ and $\mu$.

### Parameters

  * `ϑType <: Callable`: type of `ϑ`
  * `fType <: Callable`: type of `f`
  * `uType <: Callable`: type of `u`
  * `gType <: Callable`: type of `g`
  * `ϕType <: Callable`: type of `ϕ`
  * `ūType <: Callable`: type of `ū`
  * `ḡType <: Callable`: type of `ḡ`
  * `ψType <: Callable`: type of `ψ`
  * `ωType <: Callable`: type of `ω`
  * `v̄Type <: Callable`: type of `v̄`
  * `f̄Type <: Callable`: type of `f̄`
  * `lagType <: Callable`: Lagrangian type
  * `invType <: OptionalInvariants`: invariants type
  * `parType <: OptionalParameters`: parameters type
  * `perType <: OptionalPeriodicity`: periodicity type

### Fields

  * `f`: function computing the vector field
  * `u`: function computing the projection for $q$, for a degenerate system given by $\lambda$
  * `g`: function computing the projection for $p$, for a degenerate system given by $\nabla \vartheta (q) \cdot \lambda$
  * `ϕ`: primary constraints, for a degenerate system given by $p - \vartheta (t,q)$
  * `ū`: function computing the secondary projection field $\bar{u}$, for a degenerate system given by $\lambda$ (*optional*)
  * `ḡ`: function computing the secondary projection field $\bar{g}$, for a degenerate system given by $\lambda \cdot \nabla \vartheta (t,q)$ (*optional*)
  * `ψ`: secondary constraints, for a degenerate system given by $\dot{p} - \dot{q} \cdot \nabla \vartheta (t,q)$ (*optional*)
  * `ω`: function computing the symplectic matrix
  * `v̄`: function computing an initial guess for the velocity field $v$ (*optional*)
  * `f̄`: function computing an initial guess for the force field $f$ (*optional*)
  * `lagrangian`: function computing the Lagrangian $L$
  * `invariants`: functions for the computation of invariants, either a `NamedTuple` containing the equation's invariants or `NullInvariants`
  * `parameters`: type constraints for parameters, either a `NamedTuple` containing the equation's parameters or `NullParameters`
  * `periodicity`: determines the periodicity of the state vector `q` for cutting periodic solutions, either a `AbstractArray` or `NullPeriodicity`

### Constructors

```julia
LDAE(ϑ, f, u, g, ϕ, ū, ḡ, ψ, ω, v̄, f̄, lagrangian, invariants, parameters, periodicity)
LDAE(ϑ, f, u, g, ϕ, ū, ḡ, ψ, ω, lagrangian; v̄ = _ldae_default_v̄, f̄ = f, invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
LDAE(ϑ, f, u, g, ϕ, ω, lagrangian; v̄ = _ldae_default_v̄, f̄ = f, invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

where 

```julia
_ldae_default_v̄(v, t, q, params) = nothing
```

The function `ϑ` computes the momentum, `f` computes the force field, `u` and `g` compute the projections, and `ϕ` provides the algebraic constraint. The functions `ψ`, `ū` and `ḡ` are optional and provide the secondary constraint, that is the time derivative of the algebraic constraint, and the corresponding projection.

### Function Definitions

The functions `ϑ` and `f` must have the interface

```julia
function ϑ(p, t, q, v, params)
    p[1] = ...
    p[2] = ...
    ...
end

function f(f, t, q, v, params)
    f[1] = ...
    f[2] = ...
    ...
end
```

where `t` is the current time, `q` is the current solution vector, `v` is the current velocity and `f` and `p` are the vectors which hold the result of evaluating the functions $f$ and $ϑ$ on `t`, `q` and `v`. The funtions `g`, `v̄` and `f̄` are specified by

```julia
function u(u, t, q, v, p, μ, params)
    u[1] = ...
    u[2] = ...
    ...
end

function g(g, t, q, v, p, μ, params)
    g[1] = ...
    g[2] = ...
    ...
end

function v̄(v, t, q, p, params)
    v[1] = ...
    v[2] = ...
    ...
end

function f̄(f, t, q, v, params)
    f[1] = ...
    f[2] = ...
    ...
end
```

and the functions `ω` and `l`, computing the symplectic matrix and the Lagrangian, have the following signature

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

Some integrators also enforce the secondary constraint $\psi$ and require the following additional functions

```
function ū(u, t, q, v, p, μ, params)
    u[1] = ...
    u[2] = ...
    ...
end

function ḡ(g, t, q, v, p, μ, params)
    g[1] = ...
    g[2] = ...
    ...
end

function ψ(ψ, t, q, v, p, q̇, ṗ, params)
    ψ[1] = ...
end
```
