`DELEProblem`: Discrete Euler-Lagrange Equation Problem

Discrete Euler-Lagrange equations define an initial value problem of the form

$$
D_1 L_d (q_{n}, q_{n+1}) + D_2 L_d (q_{n-1}, q_{n}) = 0 ,
$$

with discrete Lagrangian $L_d$.

The dynamical variables $q$ with initial conditions $q_{0}$ and $q_{1}$ take values in $\mathbb{R}^{d}$.

### Constructors

```julia
DELEProblem(Ld, D1Ld, D2Ld, tspan, tstep, ics::NamedTuple; kwargs...)
DELEProblem(Ld, D1Ld, D2Ld, tspan, tstep, q₀::StateVariable, q₁::StateVariable; kwargs...)
DELEProblem(Ld, D1Ld, D2Ld, tspan, tstep, q₀::AbstractArray, q₁::AbstractArray; kwargs...)
```

where `Ld` is the function computing the discrete Lagrangian, `D1Ld` and `D2Ld` are functions computing the derivative of `Ld` with respect to the first and second argument, `tspan` is the time interval `(t₀,tₙ)` for the problem to be solved in, `tstep` is the time step to be used in the simulation, and `ics` is a `NamedTuple` with entries `q₀` and  `q₁` of type `StateVariable`. The initial conditions `q₀` and  `q₁` can also be prescribed directly, as a `StateVariable` or an `AbstractArray{<:Number}`.

For the interface of the functions `Ld`, `D1Ld` and `D2Ld` see [`DELE`](@ref).

For possible keyword arguments see the documentation on [`EquationProblem`](@ref GeometricEquations.EquationProblem) subtypes.

### Function Definitions

The function `Ld` providing the discrete Lagrangian must have the interface

```julia
function Ld(t_{n}, t_{n+1}, q_{n}, q_{n+1}, params)
    return ...
end
```

where `t_{n}` and `t_{n+1}` are the time of the previous and next step, `q_{n}` and `q_{n+1}` are the solution vectors of the previous and next step, and `params` is a `NamedTuple` of additional parameters on which the Lagrangian may depend. The derivatives of the discrete Lagrangian with respect to its first and second argument, `D_1 L_d` and `D_2 L_d`, respectively, must have the interfaces

```julia
function D1Ld(D, t_{n}, t_{n+1}, q_{n}, q_{n+1}, params)
    D1[1] = ...
    D1[2] = ...
    ...
end
```

and

```julia
function D2Ld(D2, t_{n}, t_{n+1}, q_{n}, q_{n+1}, params)
    D2[1] = ...
    D2[2] = ...
    ...
end
```
