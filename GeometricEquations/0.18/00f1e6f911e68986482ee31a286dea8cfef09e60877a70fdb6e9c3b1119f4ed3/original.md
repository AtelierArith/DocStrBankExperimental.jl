`PODEProblem`: Partitioned Ordinary Differential Equation Problem

A partitioned ordinary differential equation is an initial value problem of the form

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t), p(t)) , \\
\dot{p} (t) &= f(t, q(t), p(t)) ,
\end{aligned}
$$

with vector fields $v$ and $f$.

The dynamical variables $(q,p)$ with initial conditions $(q(t_{0}) = q_{0}, p(t_{0}) = p_{0})$ take values in $\mathbb{R}^{d} \times \mathbb{R}^{d}$.

### Constructors

```julia
PODEProblem(v, f, tspan, tstep, ics; kwargs...)
PODEProblem(v, f, tspan, tstep, q₀::StateVariable, p₀::StateVariable; kwargs...)
PODEProblem(v, f, tspan, tstep, q₀::AbstractArray, p₀::AbstractArray; kwargs...)
```

where `v` and `f` are the function computing the vector fields,  `tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is a `NamedTuple` with entries `q` and `p`. The initial conditions `q₀` and `p₀` can also be prescribed directly, with `StateVariable` an `AbstractArray{<:Number}`. For the interfaces of the functions `v` and `f` see [`PODE`](@ref).

For possible keyword arguments see the documentation on [`EquationProblem`](@ref GeometricEquations.EquationProblem) subtypes.

### Function Definitions

The functions `v` and `f` must have the interface

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
```

where `t` is the current time, `q` and `p` are the current solution vectors, `v` and `f` are the vectors which hold the result of evaluating the vector fields $v$ and $f$ on `t`, `q` and `p`, and params is a `NamedTuple` of additional parameters.
