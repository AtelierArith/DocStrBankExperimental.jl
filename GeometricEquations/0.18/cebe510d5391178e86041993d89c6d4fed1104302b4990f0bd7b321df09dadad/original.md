`HDAE`: Hamiltonian Differential Algebraic Equation

A Hamiltonian differential algebraic is an initial value problem, that is a canonical Hamiltonian system of equations subject to Dirac constraints,

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t), p(t)) + u(t, q(t), p(t), \lambda(t)) + \bar{u} (t, q(t), p(t), \mu(t)) , \\
\dot{p} (t) &= f(t, q(t), p(t)) + g(t, q(t), p(t), \lambda(t)) + \bar{g} (t, q(t), p(t), \mu(t)) , \\
0 &= \phi (t, q(t), p(t)) , \\
0 &= \psi (t, q(t), p(t), \dot{q}(t), \dot{p}(t)) ,
\end{aligned}
$$

with vector fields $v$, $u$, $\bar{u}$ and $f$, $g$, $\bar{g}$, primary constraint $\phi(q,p)=0$ and secondary constraint $\psi(q,p,\dot{q},\dot{p})=0$.

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
  * `hamType <: Callable`: Hamiltonian type
  * `invType <: OptionalInvariants`: invariants type
  * `parType <: OptionalParameters`: parameters type
  * `perType <: OptionalPeriodicity`: periodicity type

### Fields

  * `v`: function computing the Hamiltonian vector field $v$
  * `f`: function computing the Hamiltonian vector field $f$
  * `u`: function computing the projection for $q$
  * `g`: function computing the primary projection field $g$
  * `ϕ`: primary constraints
  * `ū`: function computing the secondary projection field $\bar{u}$ (*optional*)
  * `ḡ`: function computing the secondary projection field $\bar{g}$ (*optional*)
  * `ψ`: secondary constraints (*optional*)
  * `v̄`: function computing an initial guess for the velocity field $v$ (*optional*, defaults to `v`)
  * `f̄`: function computing an initial guess for the force field $f$ (*optional*, defaults to `f`)
  * `hamiltonian`: function computing the Hamiltonian $H$ (usually the total energy of the system)
  * `invariants`: functions for the computation of invariants, either a `NamedTuple` containing the equation's invariants or `NullInvariants`
  * `parameters`: type constraints for parameters, either a `NamedTuple` containing the equation's parameters or `NullParameters`
  * `periodicity`: determines the periodicity of the state vector `q` for cutting periodic solutions, either a `AbstractArray` or `NullPeriodicity`

### Constructors

```julia
HDAE(v, f, u, g, ϕ, ū, ḡ, ψ, h, v̄, f̄, invariants, parameters, periodicity)
HDAE(v, f, u, g, ϕ, ū, ḡ, ψ, h; kwargs...)
HDAE(v, f, u, g, ϕ, h; kwargs...)
```

The functions `v` and `f` compute the vector field, `u` and `g` compute the projections, `ϕ` provides the algebraic constraint and `h` the Hamiltonian. The functions `ψ`, `ū` and `ḡ` are optional and provide the secondary constraint, that is the time derivative of the algebraic constraint, and the corresponding projection.

### Function Definitions

The functions are defined by

The functions `v`, `f`, `u`, `g`, `ϕ` and `h` must have the interface

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

function h(t, q, p, params)
    ...
end
```

where `t` is the current time, `q`, `p`, `λ` and `μ` are the current solution vectors, `v`, `f`, `u` and `g` are the vectors which hold the result of evaluating the vector fields $v$ and $f$, the projections on the primary constraint $u$ and $g$,  `ϕ` holds the algebraic constraint $\phi$, and `h` returns the Hamiltonian of the system, all evaluated on `t`, `q`, `p` and `λ`.

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

The `HDAE` is created by

```julia
equ = HDAE(v, f, u, g, ϕ, h)
```

or

```julia
equ = HDAE(v, f, u, g, ϕ, ū, ḡ, ψ, h)
```
