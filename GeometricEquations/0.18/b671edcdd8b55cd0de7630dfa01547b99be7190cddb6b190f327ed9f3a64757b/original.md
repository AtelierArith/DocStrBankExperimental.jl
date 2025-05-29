`HDAEProblem`: Hamiltonian Differential Algebraic Equation

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

The dynamical variables $(q,p)$ with initial conditions $(q(t_{0}) = q_{0}, p(t_{0}) = p_{0})$ take values in $\mathbb{R}^{d} \times \mathbb{R}^{d}$. The algebraic variables $(λ,μ)$ with initial condition $(λ(t_{0}) = λ_{0}, μ(t_{0}) = μ_{0})$ take values in $\mathbb{R}^{m} \times \mathbb{R}^{m}$.

### Constructors

```julia
HDAEProblem(v, f, u, g, ϕ, ū, ḡ, ψ, h, tspan, tstep, ics::NamedTuple; kwargs...)
HDAEProblem(v, f, u, g, ϕ, ū, ḡ, ψ, h, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::StateVariable, μ₀::StateVariable = zero(λ₀); kwargs...)
HDAEProblem(v, f, u, g, ϕ, h, tspan, tstep, ics::NamedTuple; kwargs...)
HDAEProblem(v, f, u, g, ϕ, h, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::StateVariable; kwargs...)
```

The functions `v` and `f` compute the vector field, `u` and `g` compute the projections, `ϕ` provides the algebraic constraint and `h` the Hamiltonian. The functions `ψ`, `ū` and `ḡ` are optional and provide the secondary constraint, that is the time derivative of the algebraic constraint, and the corresponding projection.

`tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is a `NamedTuple` with entries `q`, `p`, `λ` and `μ`. The initial conditions `q₀`, `p₀`, `λ₀` and `μ₀` can also be prescribed directly, with `StateVariable` an `AbstractArray{<:Number}`. For the interfaces of the functions `v`, `f`, `u`, `g`, `ϕ`, `ū`, `ḡ`, `ψ`, and `h` see [`HDAE`](@ref).

In addition to the standard keyword arguments for [`EquationProblem`](@ref GeometricEquations.EquationProblem) subtypes, a `HDAEProblem` accepts functions `v̄` and `f̄` for the computation of initial guesses for the vector fields with default values `v̄ = v` and `f̄ = f`.

### Function Definitions

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

With the above function definitions the `HDAEProblem` can be created by

```julia
tspan = (0.0, 1.0)
tstep = 0.1
q₀ = [1., 1.]
p₀ = [1., 0.]
λ₀ = [0.]
μ₀ = [0.]

prob = HDAEProblem(v, f, u, g, ϕ, h, tspan, tstep, q₀, p₀, λ₀)
```

or

```julia
prob = HDAEProblem(v, f, u, g, ϕ, ū, ḡ, ψ, h, tspan, tstep, q₀, p₀, λ₀, μ₀)
```
