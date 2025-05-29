```julia
get_non_stochastic_steady_state_residuals(
    𝓂,
    values;
    parameters,
    tol,
    verbose
)

```

Calculate the residuals of the non-stochastic steady state equations of the model for a given set of values. Values not provided, will be filled with the non-stochastic steady state values corresponding to the current parameters.

# Arguments

  * `𝓂`: object created by [`@model`](@ref) and [`@parameters`](@ref).
  * `values` [Type: `Union{Vector{Float64}, Dict{Symbol, Float64}, Dict{String, Float64}, KeyedArray{Float64, 1}}`]: A Vector, Dict, or KeyedArray containing the values of the variables and calibrated parameters in the non-stochastic steady state equations (including calibration equations).

# Keyword Arguments

  * `parameters` [Default: `nothing`]: If `nothing` is provided, the solution is calculated for the parameters defined previously. Acceptable inputs are a `Vector` of parameter values, a `Vector` or `Tuple` of `Pair`s of the parameter `Symbol` or `String` and value. If the new parameter values differ from the previously defined the solution will be recalculated.
  * `tol` [Default: `Tolerances()`, Type: `Tolerances`]: define various tolerances for the algorithm used to solve the model. See documentation of [`Tolerances`](@ref) for more details: `?Tolerances`
  * `verbose` [Default: `false`, Type: `Bool`]: print information about results of the different solvers used to solve the model (non stochastic steady state solver, Sylvester equations, Lyapunov equation, and quadratic matrix equation).

# Returns

  * `KeyedArray` containing the absolute values of the residuals of the non-stochastic steady state equations.

# Examples

```jldoctest
using MacroModelling

@model RBC begin
    1  /  c[0] = (β  /  c[1]) * (α * exp(z[1]) * k[0]^(α - 1) + (1 - δ))
    c[0] + k[0] = (1 - δ) * k[-1] + q[0]
    q[0] = exp(z[0]) * k[-1]^α
    z[0] = ρ * z[-1] + std_z * eps_z[x]
end

@parameters RBC begin
    std_z = 0.01
    ρ = 0.2
    δ = 0.02
    k[ss] / q[ss] = 2.5 | α
    β = 0.95
end

steady_state = SS(RBC, derivatives = false)

get_non_stochastic_steady_state_residuals(RBC, steady_state)
# output
1-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Equation ∈ 5-element Vector{Symbol}
And data, 5-element Vector{Float64}:
 (:Equation₁)             0.0
 (:Equation₂)             0.0
 (:Equation₃)             0.0
 (:Equation₄)             0.0
 (:CalibrationEquation₁)  0.0

get_non_stochastic_steady_state_residuals(RBC, [1.1641597, 3.0635781, 1.2254312, 0.0, 0.18157895])
# output
1-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Equation ∈ 5-element Vector{Symbol}
And data, 5-element Vector{Float64}:
 (:Equation₁)             2.7360991250446887e-10
 (:Equation₂)             6.199999980083248e-8
 (:Equation₃)             2.7897102183871425e-8
 (:Equation₄)             0.0
 (:CalibrationEquation₁)  8.160392850342646e-8
```
