```julia
get_irf(
    𝓂;
    periods,
    algorithm,
    parameters,
    variables,
    shocks,
    negative_shock,
    generalised_irf,
    initial_state,
    levels,
    shock_size,
    ignore_obc,
    verbose,
    tol,
    quadratic_matrix_equation_algorithm,
    sylvester_algorithm,
    lyapunov_algorithm
)

```

Return impulse response functions (IRFs) of the model. By default, the values represent absolute deviations from the relevant steady state (see `levels` for details). The non-stochastic steady state (NSSS) is relevant for first order solutions and the stochastic steady state for higher order solutions.

If the model contains occasionally binding constraints and `ignore_obc = false` they are enforced using shocks.

# Arguments

  * `𝓂`: object created by [`@model`](@ref) and [`@parameters`](@ref).

# Keyword Arguments

  * `periods` [Default: `40`, Type: `Int`]: number of periods for which to calculate the output. In case a matrix of shocks was provided, periods defines how many periods after the series of shocks the output continues.
  * `algorithm` [Default: `:first_order`, Type: `Symbol`]: algorithm to solve for the dynamics of the model. Available algorithms: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `parameters` [Default: `nothing`]: If `nothing` is provided, the solution is calculated for the parameters defined previously. Acceptable inputs are a `Vector` of parameter values, a `Vector` or `Tuple` of `Pair`s of the parameter `Symbol` or `String` and value. If the new parameter values differ from the previously defined the solution will be recalculated.
  * `variables` [Default: `:all_excluding_obc`]: variables for which to show the results. Inputs can be a variable name passed on as either a `Symbol` or `String` (e.g. `:y` or "y"), or `Tuple`, `Matrix` or `Vector` of `String` or `Symbol`. Any variables not part of the model will trigger a warning. `:all_excluding_auxilliary_and_obc` contains all shocks less those related to auxilliary variables and related to occasionally binding constraints (obc). `:all_excluding_obc` contains all shocks less those related to auxilliary variables. `:all` will contain all variables.
  * `shocks` [Default: `:all_excluding_obc`]: shocks for which to calculate the IRFs. Inputs can be a shock name passed on as either a `Symbol` or `String` (e.g. `:y`, or "y"), or `Tuple`, `Matrix` or `Vector` of `String` or `Symbol`. `:simulate` triggers random draws of all shocks (excluding occasionally binding constraints (obc) related shocks). `:all_excluding_obc` will contain all shocks but not the obc related ones. `:all` will contain also the obc related shocks. A series of shocks can be passed on using either a `Matrix{Float64}`, or a `KeyedArray{Float64}` as input with shocks (`Symbol` or `String`) in rows and periods in columns. The period of the simulation will correspond to the length of the input in the period dimension + the number of periods defined in `periods`. If the series of shocks is input as a `KeyedArray{Float64}` make sure to name the rows with valid shock names of type `Symbol`. Any shocks not part of the model will trigger a warning. `:none` in combination with an `initial_state` can be used for deterministic simulations.
  * `negative_shock` [Default: `false`, Type: `Bool`]: calculate IRFs for a negative shock.
  * `generalised_irf` [Default: `false`, Type: `Bool`]: calculate generalised IRFs. Relevant for nonlinear (higher order perturbation) solutions only. Reference steady state for deviations is the stochastic steady state. `initial_state` has no effect on generalised IRFs. Occasionally binding constraint are not respected for generalised IRF.
  * `initial_state` [Default: `[0.0]`, Type: `Union{Vector{Vector{Float64}},Vector{Float64}}`]: The initial state defines the starting point for the model. In the case of pruned solution algorithms the initial state can be given as multiple state vectors (`Vector{Vector{Float64}}`). In this case the initial state must be given in deviations from the non-stochastic steady state. In all other cases the initial state must be given in levels. If a pruned solution algorithm is selected and `initial_state` is a `Vector{Float64}` then it impacts the first order initial state vector only. The state includes all variables as well as exogenous variables in leads or lags if present. `get_irf(𝓂, shocks = :none, variables = :all, periods = 1)` returns a `KeyedArray` with all variables.
  * `levels` [Default: `false`, Type: `Bool`]: return levels or absolute deviations from the relevant steady state corresponding to the solution algorithm (e.g. stochastic steady state for higher order solution algorithms).
  * `shock_size` [Default: `1`, Type: `Real`]: affects the size of shocks as long as they are not set to `:none`.
  * `ignore_obc` [Default: `false`, Type: `Bool`]: solve the model ignoring the occasionally binding constraints.
  * `quadratic_matrix_equation_algorithm` [Default: `:schur`, Type: `Symbol`]: algorithm to solve quadratic matrix equation (`A * X ^ 2 + B * X + C = 0`). Available algorithms: `:schur`, `:doubling`
  * `sylvester_algorithm` [Default: function of size of problem, with smaller problems: `:doubling`, and larger problems: `:bicgstab`, Type: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: algorithm to solve Sylvester equation (`A * X * B + C = X`). Available algorithms: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`. Input argument can be up to two elements in a `Vector` or `Tuple`. The first (second) element corresponds to the second (third) order perturbation solutions' Sylvester equation. If only one element is provided it corresponds to the second order perturbation solutions' Sylvester equation.
  * `lyapunov_algorithm` [Default: `:doubling`, Type: `Symbol`]: algorithm to solve Lyapunov equation (`A * X * A' + C = X`). Available algorithms: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `tol` [Default: `Tolerances()`, Type: `Tolerances`]: define various tolerances for the algorithm used to solve the model. See documentation of [`Tolerances`](@ref) for more details: `?Tolerances`
  * `verbose` [Default: `false`, Type: `Bool`]: print information about results of the different solvers used to solve the model (non stochastic steady state solver, Sylvester equations, Lyapunov equation, and quadratic matrix equation).

# Returns

  * `KeyedArray` with variables in rows, periods in columns, and shocks as the third dimension.

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

get_irf(RBC)
# output
3-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Variables ∈ 4-element Vector{Symbol}
→   Periods ∈ 40-element UnitRange{Int64}
◪   Shocks ∈ 1-element Vector{Symbol}
And data, 4×40×1 Array{Float64, 3}:
[:, :, 1] ~ (:, :, :eps_z):
        (1)           (2)           …  (39)            (40)
  (:c)    0.00674687    0.00729773        0.00146962      0.00140619
  (:k)    0.0620937     0.0718322         0.0146789       0.0140453
  (:q)    0.0688406     0.0182781         0.00111425      0.00106615
  (:z)    0.01          0.002             2.74878e-29     5.49756e-30
```
