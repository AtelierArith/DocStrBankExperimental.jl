`DAEProblem`: Differential Algebraic Equation Problem

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

The dynamical variable $q$ with initial conditions $q(t_{0}) = q_{0}$ takes values in $\mathbb{R}^{d}$. The algebraic variables $(λ,μ)$ with initial condition $(λ(t_{0}) = λ_{0}, μ(t_{0}) = μ_{0})$ take values in $\mathbb{R}^{m} \times \mathbb{R}^{m}$.

### Constructors

```julia
DAEProblem(v, u, ϕ, ū, ψ, tspan, tstep, ics::NamedTuple; kwargs...)
DAEProblem(v, u, ϕ, ū, ψ, tspan, tstep, q₀::StateVariable, λ₀::StateVariable, μ₀::StateVariable = zero(λ₀); kwargs...)
DAEProblem(v, u, ϕ, tspan, tstep, ics::NamedTuple; kwargs...)
DAEProblem(v, u, ϕ, tspan, tstep, q₀::StateVariable, λ₀::StateVariable; kwargs...)
```

The functions `v` and `u` compute the vector field and the projection, respectively, `ϕ` provides the algebraic constraint. The functions `ψ` and `ū` are optional and provide the secondary constraint, that is the time derivative of the algebraic constraint, and the corresponding projection.

`tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is a `NamedTuple` with entries `q`, `λ` and `μ`. The initial conditions `q₀`, `λ₀` and `μ₀` can also be prescribed directly, with `StateVariable` an `AbstractArray{<:Number}`. For the interfaces of the functions `v`, `u`, `ϕ`, `ū`, `ψ` see [`DAE`](@ref).

In addition to the standard keyword arguments for [`EquationProblem`](@ref GeometricEquations.EquationProblem) subtypes, a `DAEProblem` accepts a function `v̄` for the computation of an initial guess for the vector field with default value `v̄ = v`.

### Function Definitions

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

With the above function definitions the `DAEProblem` can be created by

```julia
tspan = (0.0, 1.0)
tstep = 0.1
q₀ = [1., 1.]
λ₀ = [0.]
μ₀ = [0.]

prob = DAEProblem(v, u, ϕ, tspan, tstep, q₀, λ₀)
```

or

```julia
prob = DAEProblem(v, u, ϕ, ū, ψ, tspan, tstep, q₀, λ₀, μ₀)
```
