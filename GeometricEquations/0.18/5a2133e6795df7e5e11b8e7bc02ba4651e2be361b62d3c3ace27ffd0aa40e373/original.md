`HODEProblem`: Hamiltonian Ordinary Differential Equation Problem

A canonical Hamiltonian system of equations is special case of a partitioned ordinary differential equation,

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t), p(t)) , \\
\dot{p} (t) &= f(t, q(t), p(t)) ,
\end{aligned}
$$

with vector fields $v$ and $f$, given by

$$
\begin{aligned}
v &=   \frac{\partial H}{\partial p} , &
f &= - \frac{\partial H}{\partial q} .
\end{aligned}
$$

The dynamical variables $(q,p)$ with initial conditions $(q(t_{0}) = q_{0}, p(t_{0}) = p_{0})$ take values in $T^{*} Q \simeq \mathbb{R}^{d} \times \mathbb{R}^{d}$.

### Constructors

```julia
HODEProblem(v, f, hamiltonian, tspan, tstep, ics; kwargs...)
HODEProblem(v, f, hamiltonian, tspan, tstep, q₀::StateVariable, p₀::StateVariable; kwargs...)
HODEProblem(v, f, hamiltonian, tspan, tstep, q₀::AbstractArray, p₀::AbstractArray; kwargs...)
```

where `v` and `f` are the function computing the vector fields,  `hamiltonian` returns the value of the Hamiltonian (i.e. the total energy), `tspan` is the time interval `(t₀,t₁)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is a `NamedTuple` with entries `q` and `p`. The initial conditions `q₀` and `p₀` can also be prescribed directly, with `StateVariable` an `AbstractArray{<:Number}`. For the interfaces of the functions `v`, `f` and `hamiltonian` see [`HODE`](@ref).

For possible keyword arguments see the documentation on [`EquationProblem`](@ref GeometricEquations.EquationProblem) subtypes.

### Function Definitions

The functions `v`, `f` and `hamiltonian` must have the interface

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

function hamiltonian(t, q, p, params)
    return ...
end
```

where `t` is the current time, `q` and `p` are the current solution vectors, `v` and `f` are the vectors which hold the result of evaluating the vector fields on `t`, `q` and `p`, and params is a `NamedTuple` of additional parameters.
