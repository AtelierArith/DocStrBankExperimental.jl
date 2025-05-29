`SPSDEProblem`: Stratonovich Split Partitioned Stochastic Differential Equation Problem

Defines a partitioned stochastic differential initial value problem

$$
\begin{aligned}
dq (t) &=   v(t, q(t), p(t)) \, dt + B(t, q(t), p(t)) \circ dW , & q(t_{0}) &= q_{0} , \\
dp (t) &= [ f_1(t, q(t), p(t)) + f_2(t, q(t), p(t)) ] \, dt + [ G_1(t, q(t), p(t)) + G_2(t, q(t), p(t)) ] \circ dW , & p(t_{0}) &= p_{0} ,
\end{aligned}
$$

with the drift vector fields $v$ and $f_i$, diffusion matrices $B$ and $G_i$, initial conditions $q_{0}$ and $p_{0}$, the dynamical variables $(q,p)$ taking values in $\mathbb{R}^{d} \times \mathbb{R}^{d}$, and the m-dimensional Wiener process W

### Constructors

```julia
SPSDEProblem(v, f1, f2, B, G1, G2, tspan, tstep, ics::NamedTuple; kwargs...)
SPSDEProblem(v, f1, f2, B, G1, G2, tspan, tstep, q₀::StateVariable; p₀::StateVariable; kwargs...)
```

where `v` and `f` are the functions computing the vector field and `Bᵢ` and `Gᵢ` compute the diffusion matrices, `tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is a `NamedTuple` with entry `q`. The initial condition `q₀` can also be prescribed directly, with `StateVariable` an `AbstractArray{<:Number}`.

For possible keyword arguments see the documentation on [`EquationProblem`](@ref GeometricEquations.EquationProblem) subtypes.

### Function Definitions

The functions `v`, `f1`, `f2`, `B`, `G1` and `G2`, providing the drift vector fields and diffusion matrices, all take five arguments, `(out, t, q, p, params)`.

```julia
function v(v, t, q, p, params)
    v[1] = ...
    v[2] = ...
    ...
end

function f1(f, t, q, p, params)
    f[1] = ...
    f[2] = ...
    ...
end

function f2(f, t, q, p, params)
    f[1] = ...
    f[2] = ...
    ...
end

function B(B, t, q, p, params)
    B[1,1] = ...
    ...
end

function G1(G, t, q, p, params)
    G[1,1] = ...
    ...
end

function G2(G, t, q, p, params)
    G[1,1] = ...
    ...
end
```

where `t` is the current time, `(q,p)` is the current solution vector, and `v`, `f`, `B` and `G` are the variables which hold the result of evaluating the vector fields $v$, $f$ and the matrices $B_i$, $G_i$ on `(t,q,p)`.
