`PDAE`: Partitioned Differential Algebraic Equation

A partitioned differential algebraic equation has the form

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t), p(t)) + u(t, q(t), p(t), \lambda(t)) , \\
\dot{p} (t) &= f(t, q(t), p(t)) + g(t, q(t), p(t), \lambda(t)) , \\
0 &= \phi (t, q(t), p(t)) ,
\end{aligned}
$$

with vector fields $v$ and $f$, projection $u$ and $g$, algebraic constraint $\phi=0$.

Some integrators also enforce the secondary constraint $\psi$, that is the time derivative of the algebraic constraint $\phi$. In this case, the system of equations is modified as follows

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t), p(t)) + u(t, q(t), p(t), \lambda(t)) + \bar{u} (t, q(t), p(t), \mu(t)) , \\
\dot{p} (t) &= f(t, q(t), p(t)) + g(t, q(t), p(t), \lambda(t)) + \bar{g} (t, q(t), p(t), \mu(t)) , \\
0 &= \phi (t, q(t), p(t)) , \\
0 &= \psi (t, q(t), p(t), \dot{q} (t), \dot{p} (t)) .
\end{aligned}
$$

### Parameters

  * `vType <: Callable`: type of `v`
  * `fType <: Callable`: type of `f`
  * `uType <: Callable`: type of `u`
  * `gType <: Callable`: type of `g`
  * `ϕType <: Callable`: type of `ϕ`
  * `ūType <: Callable`: type of `ū`
  * `ḡType <: Callable`: type of `ḡ`
  * `ψType <: Callable`: type of `ψ`
  * `v̄Type <: Callable`: type of `v̄`
  * `f̄Type <: Callable`: type of `f̄`
  * `invType <: OptionalInvariants`: invariants type
  * `parType <: OptionalParameters`: parameters type
  * `perType <: OptionalPeriodicity`: periodicity type

### Fields

  * `v`: function computing the vector field $v$
  * `f`: function computing the vector field $f$
  * `u`: function computing the projection for $q$
  * `g`: function computing the projection for $p$
  * `ϕ`: algebraic constraints
  * `ū`: function computing the secondary projection field $\bar{u}$ (*optional*)
  * `ḡ`: function computing the secondary projection field $\bar{g}$ (*optional*)
  * `ψ`: secondary constraints (*optional*)
  * `v̄`: function computing an initial guess for the velocity field $v$ (*optional*, defaults to `v`)
  * `f̄`: function computing an initial guess for the force field $f$ (*optional*, defaults to `f`)
  * `invariants`: functions for the computation of invariants, either a `NamedTuple` containing the equation's invariants or `NullInvariants`
  * `parameters`: type constraints for parameters, either a `NamedTuple` containing the equation's parameters or `NullParameters`
  * `periodicity`: determines the periodicity of the state vector `q` for cutting periodic solutions, either a `AbstractArray` or `NullPeriodicity`

### Constructors

```julia
PDAE(v, f, u, g, ϕ, ū, ḡ, ψ, v̄, f̄, invariants, parameters, periodicity)
PDAE(v, f, u, g, ϕ, ū, ḡ, ψ; kwargs...)
PDAE(v, f, u, g, ϕ; kwargs...)
```

The functions `v` and `f` compute the vector field, `u` and `g` compute the projections, and `ϕ` provides the algebraic constraint. The functions `ψ`, `ū` and `ḡ` are optional and provide the secondary constraint and the corresponding projection.

### Function Definitions

The functions are defined by

The functions `v`, `f`, `u`, `g` and `ϕ` must have the interface

```julia
function v(v, t, q, p, params)
    v[1] = ...
    v[2] = ...
    ...
end

function f(g, t, q, p, params)
    f[1] = ...
    f[2] = ...
    ...
end

function u(u, t, q, p, λ, params)
    u[1] = ...
    u[2] = ...
    ...
end

function g(g, t, q, p, λ, params)
    g[1] = ...
    g[2] = ...
    ...
end

function ϕ(ϕ, t, q, p, params)
    ϕ[1] = ...
end
```

where `t` is the current time, `q`, `p` and `λ` are the current solution vectors, `v`, `f`, `u` and `g` are the vectors which hold the result of evaluating the vector fields $v$ and $f$, the projections $u$ and $g$, and `ϕ` holds the algebraic constraint $\phi$, evaluated on `t`, `q`, `p` and `λ`.

Some integrators also enforce the secondary constraint $\psi$ and require the following additional functions

```
function ū(u, t, q, p, μ, params)
    u[1] = ...
    u[2] = ...
    ...
end

function ḡ(g, t, q, p, μ, params)
    g[1] = ...
    g[2] = ...
    ...
end

function ψ(ψ, t, q, p, v, f, params)
    ψ[1] = ...
end
```

The `PDAE` is created by

```julia
equ = PDAE(v, f, u, g, ϕ)
```

or

```julia
equ = PDAE(v, f, u, g, ϕ, ū, ḡ, ψ)
```
