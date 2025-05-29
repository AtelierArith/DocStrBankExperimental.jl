`PSDEProblem`: Stratonovich Partitioned Stochastic Differential Equation Problem

A partitioned stochastic differential equations is an initial value problem of the form

$$
\begin{aligned}
dq (t) &= v(t, q(t), p(t)) \, dt + B(t, q(t), p(t)) \circ dW , & q(t_{0}) &= q_{0} , \\
dp (t) &= f(t, q(t), p(t)) \, dt + G(t, q(t), p(t)) \circ dW , & p(t_{0}) &= p_{0}
\end{aligned}
$$

with the drift vector fields $v$ and $f$, diffusion matrices $B$ and $G$, initial conditions $q_{0}$ and $p_{0}$, the dynamical variables $(q,p)$ taking values in $\mathbb{R}^{d} \times \mathbb{R}^{d}$, and the m-dimensional Wiener process W

### Constructors

```julia
PSDEProblem(v, f, B, G, tspan, tstep, ics::NamedTuple; kwargs...)
PSDEProblem(v, f, B, G, tspan, tstep, q₀::StateVariable; p₀::StateVariable; kwargs...)
```

where `v` and `f` are the functions computing the vector field and `B` and `G` compute the diffusion matrices, `tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is a `NamedTuple` with entry `q`. The initial condition `q₀` can also be prescribed directly, with `StateVariable` an `AbstractArray{<:Number}`.

For possible keyword arguments see the documentation on [`EquationProblem`](@ref GeometricEquations.EquationProblem) subtypes.

### Function Definitions

The functions `v`, `f`, `B` and `G`, providing the drift vector fields and diffusion matrices, each take five arguments, `v(v, t, q, p, params)`, `f(f, t, q, p, params)`, `B(B, t, q, p, params)` and `G(G, t, q, p, params)`, where `t` is the current time, `(q, p)` is the current solution, and `v`, `f`, `B` and `G` are the variables which hold the result of evaluating the vector fields $v$, $f$ and the matrices $B$, $G$ on `t` and `(q,p)`, and `params` are optional parameters.

The corresponding methods should have the following signatures:

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

function B(B, t, q, p, params)
    B[1,1] = ...
    ...
end

function G(G, t, q, p, params)
    G[1,1] = ...
    ...
end
```
