`DAE`: Differential Algebraic Equation

Defines a differential algebraic initial value problem

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t)) + u(t, q(t), \lambda(t)) , \\
0 &= \phi (t, q(t)) ,
\end{aligned}
$$

with vector field $v$, projection $u$, algebraic constraint $\phi=0$.

Some integrators also enforce the secondary constraint $\psi$, that is the time derivative of the algebraic constraint $\phi$. In this case, the system of equations is modified as follows

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t)) + u(t, q(t), \lambda(t)) + \bar{u} (t, q(t), \dot{q} (t), \dot{p} (t), \mu(t)) , \\
0 &= \phi (t, q(t)) , \\
0 &= \psi (t, q(t), \dot{q} (t)) .
\end{aligned}
$$

### Parameters

  * `vType <: Callable`: type of `v`
  * `uType <: Callable`: type of `u`
  * `ϕType <: Callable`: type of `ϕ`
  * `ūType <: OptionalCallable`: type of `ū`
  * `ψType <: OptionalCallable`: type of `ψ`
  * `v̄Type <: Callable`: type of `v̄`
  * `invType <: OptionalInvariants`: invariants type
  * `parType <: OptionalParameters`: parameters type
  * `perType <: OptionalPeriodicity`: periodicity type

### Fields

  * `v`: function computing the vector field `v(v, t, q, params)`
  * `u`: function computing the projection `u(u, t, q, λ, params)`
  * `ϕ`: algebraic constraint `ϕ(ϕ, t, q, params)`
  * `ū`: function computing the secondary projection field `ū(ū, t, q, λ, params)` (*optional*)
  * `ψ`: secondary constraint `ψ(ψ, t, q, v, params)` (*optional*)
  * `v̄`: function computing an initial guess for the velocity field $v$ (defaults to `v`)
  * `invariants`: functions for the computation of invariants, either a `NamedTuple` containing the equation's invariants or `NullInvariants`
  * `parameters`: type constraints for parameters, either a `NamedTuple` containing the equation's parameters or `NullParameters`
  * `periodicity`: determines the periodicity of the state vector `q` for cutting periodic solutions, either a `AbstractArray` or `NullPeriodicity`

### Constructors

```julia
DAE(v, u, ϕ, ū, ψ, v̄, invariants, parameters, periodicity)
DAE(v, u, ϕ, ū, ψ; kwargs...)
DAE(v, u, ϕ; kwargs...)
```

The functions `v` and `u` compute the vector field and the projection, respectively, `ϕ` provides the algebraic constraint. The functions `ψ` and `ū` are optional and provide the secondary constraint, that is the time derivative of the algebraic constraint, and the corresponding projection.

### Function Definitions

The functions are defined by

The functions `v`, `u` and `ϕ` must have the interface

```julia
function v(v, t, q, params)
    v[1] = ...
    v[2] = ...
    ...
end

function u(u, t, q, λ, params)
    u[1] = ...
    u[2] = ...
    ...
end

function ϕ(ϕ, t, q, params)
    ϕ[1] = ...
end
```

where `t` is the current time, `q` and `λ` are the current solution vectors, and `v`, `u` and `ϕ` are the vectors which hold the result of evaluating the vector field $v$, the projection $u$ and the algebraic constraint $\phi$ on `t`, `q` and `λ`.

Some integrators also enforce the secondary constraint $\psi$ and require the following additional functions

```
function ū(u, t, q, μ, params)
    u[1] = ...
    u[2] = ...
    ...
end

function ψ(ψ, t, q, v, params)
    ψ[1] = ...
end
```

The `DAE` is created by

```julia
equ = DAE(v, u, ϕ)
```

or

```julia
equ = DAE(v, u, ϕ, ū, ψ)
```
