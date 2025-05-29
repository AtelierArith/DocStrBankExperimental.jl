```julia
get_irf(
    𝓂,
    parameters;
    periods,
    variables,
    shocks,
    negative_shock,
    initial_state,
    levels,
    verbose,
    tol,
    quadratic_matrix_equation_algorithm
)

```

Return impulse response functions (IRFs) of the model. Function to use when differentiating IRFs with repect to parameters.

If occasionally binding constraints are present in the model, they are not taken into account here. 

# Arguments

  * `𝓂`: object created by [`@model`](@ref) and [`@parameters`](@ref).
  * `parameters` [Type: `Vector`]: Parameter values in alphabetical order (sorted by parameter name).

# Keyword Arguments

  * `periods` [Default: `40`, Type: `Int`]: number of periods for which to calculate the output. In case a matrix of shocks was provided, periods defines how many periods after the series of shocks the output continues.
  * `variables` [Default: `:all_excluding_obc`]: variables for which to show the results. Inputs can be a variable name passed on as either a `Symbol` or `String` (e.g. `:y` or "y"), or `Tuple`, `Matrix` or `Vector` of `String` or `Symbol`. Any variables not part of the model will trigger a warning. `:all_excluding_auxilliary_and_obc` contains all shocks less those related to auxilliary variables and related to occasionally binding constraints (obc). `:all_excluding_obc` contains all shocks less those related to auxilliary variables. `:all` will contain all variables.
  * `shocks` [Default: `:all_excluding_obc`]: shocks for which to calculate the IRFs. Inputs can be a shock name passed on as either a `Symbol` or `String` (e.g. `:y`, or "y"), or `Tuple`, `Matrix` or `Vector` of `String` or `Symbol`. `:simulate` triggers random draws of all shocks (excluding occasionally binding constraints (obc) related shocks). `:all_excluding_obc` will contain all shocks but not the obc related ones. `:all` will contain also the obc related shocks. A series of shocks can be passed on using either a `Matrix{Float64}`, or a `KeyedArray{Float64}` as input with shocks (`Symbol` or `String`) in rows and periods in columns. The period of the simulation will correspond to the length of the input in the period dimension + the number of periods defined in `periods`. If the series of shocks is input as a `KeyedArray{Float64}` make sure to name the rows with valid shock names of type `Symbol`. Any shocks not part of the model will trigger a warning. `:none` in combination with an `initial_state` can be used for deterministic simulations.
  * `negative_shock` [Default: `false`, Type: `Bool`]: calculate IRFs for a negative shock.
  * `initial_state` [Default: `[0.0]`, Type: `Vector{Float64}`]: The initial state defines the starting point for the model (in levels, not deviations). The state includes all variables as well as exogenous variables in leads or lags if present. `get_irf(𝓂, shocks = :none, variables = :all, periods = 1)` returns a `KeyedArray` with all variables.
  * `levels` [Default: `false`, Type: `Bool`]: return levels or absolute deviations from the relevant steady state corresponding to the solution algorithm (e.g. stochastic steady state for higher order solution algorithms).
  * `quadratic_matrix_equation_algorithm` [Default: `:schur`, Type: `Symbol`]: algorithm to solve quadratic matrix equation (`A * X ^ 2 + B * X + C = 0`). Available algorithms: `:schur`, `:doubling`
  * `tol` [Default: `Tolerances()`, Type: `Tolerances`]: define various tolerances for the algorithm used to solve the model. See documentation of [`Tolerances`](@ref) for more details: `?Tolerances`
  * `verbose` [Default: `false`, Type: `Bool`]: print information about results of the different solvers used to solve the model (non stochastic steady state solver, Sylvester equations, Lyapunov equation, and quadratic matrix equation).

# Returns

  * `Array{<:AbstractFloat, 3}` with variables in rows, periods in columns, and shocks as the third dimension.

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
    α = 0.5
    β = 0.95
end

get_irf(RBC, RBC.parameter_values)
# output
4×40×1 Array{Float64, 3}:
[:, :, 1] =
 0.00674687  0.00729773  0.00715114  0.00687615  …  0.00146962   0.00140619
 0.0620937   0.0718322   0.0712153   0.0686381      0.0146789    0.0140453
 0.0688406   0.0182781   0.00797091  0.0057232      0.00111425   0.00106615
 0.01        0.002       0.0004      8.0e-5         2.74878e-29  5.49756e-30
```
