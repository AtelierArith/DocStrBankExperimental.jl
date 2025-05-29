`PDAEProblem`: Partitioned Differential Algebraic Equation Problem

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

The dynamical variables $(q,p)$ with initial conditions $(q(t_{0}) = q_{0}, p(t_{0}) = p_{0})$ take values in $\mathbb{R}^{d} \times \mathbb{R}^{d}$. The algebraic variables $(λ,μ)$ with initial condition $(λ(t_{0}) = λ_{0}, μ(t_{0}) = μ_{0})$ take values in $\mathbb{R}^{m} \times \mathbb{R}^{m}$.

### Constructors

```julia
PDAEProblem(v, f, u, g, ϕ, ū, ḡ, ψ, tspan, tstep, ics::NamedTuple; kwargs...)
PDAEProblem(v, f, u, g, ϕ, ū, ḡ, ψ, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::StateVariable, μ₀::StateVariable = zero(λ₀); kwargs...)
PDAEProblem(v, f, u, g, ϕ, tspan, tstep, ics::NamedTuple; kwargs...)
PDAEProblem(v, f, u, g, ϕ, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::StateVariable; kwargs...)
```

The functions `v` and `f` compute the vector field, `u` and `g` compute the projections, and `ϕ` provides the algebraic constraint. The functions `ψ`, `ū` and `ḡ` are optional and provide the secondary constraint and the corresponding projection.

`tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is a `NamedTuple` with entries `q`, `p`, `λ` and `μ`. The initial conditions `q₀`, `p₀`, `λ₀` and `μ₀` can also be prescribed directly, with `StateVariable` an `AbstractArray{<:Number}`. For the interfaces of the functions `v`, `f`, `u`, `g`, `ϕ`, `ū`, `ḡ`, `ψ` see [`PDAE`](@ref).

In addition to the standard keyword arguments for [`EquationProblem`](@ref GeometricEquations.EquationProblem) subtypes, a `PDAEProblem` accepts functions `v̄` and `f̄` for the computation of initial guesses for the vector fields with default values `v̄ = v` and `f̄ = f`.

### Function Definitions

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

With the above function definitions the `PDAEProblem` can be created by

```julia
tspan = (0.0, 1.0)
tstep = 0.1
q₀ = [1., 1.]
p₀ = [1., 0.]
λ₀ = [0.]
μ₀ = [0.]

prob = PDAEProblem(v, f, u, g, ϕ, tspan, tstep, q₀, p₀, λ₀)
```

or

```julia
prob = PDAEProblem(v, f, u, g, ϕ, ū, ḡ, ψ, tspan, tstep, q₀, p₀, λ₀, μ₀)
```
