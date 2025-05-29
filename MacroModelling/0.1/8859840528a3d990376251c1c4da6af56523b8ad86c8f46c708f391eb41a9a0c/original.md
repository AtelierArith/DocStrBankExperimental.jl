```julia
get_estimated_variables(
    𝓂,
    data;
    parameters,
    algorithm,
    filter,
    warmup_iterations,
    data_in_levels,
    levels,
    smooth,
    verbose,
    tol,
    quadratic_matrix_equation_algorithm,
    sylvester_algorithm,
    lyapunov_algorithm
)

```

Return the estimated variables (in levels by default, see `levels` keyword argument) based on the inversion filter (depending on the `filter` keyword argument), or Kalman filter or smoother (depending on the `smooth` keyword argument) using the provided data and (non-)linear solution of the model. Data is by default assumed to be in levels unless `data_in_levels` is set to `false`.

If occasionally binding constraints are present in the model, they are not taken into account here. 

# Arguments

  * `𝓂`: object created by [`@model`](@ref) and [`@parameters`](@ref).
  * `data` [Type: `KeyedArray`]: data matrix with variables (`String` or `Symbol`) in rows and time in columns

# Keyword Arguments

  * `parameters` [Default: `nothing`]: If `nothing` is provided, the solution is calculated for the parameters defined previously. Acceptable inputs are a `Vector` of parameter values, a `Vector` or `Tuple` of `Pair`s of the parameter `Symbol` or `String` and value. If the new parameter values differ from the previously defined the solution will be recalculated.
  * `algorithm` [Default: `:first_order`, Type: `Symbol`]: algorithm to solve for the dynamics of the model. Available algorithms: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `filter` [Default: `:kalman`, Type: `Symbol`]: filter used to compute the variables, and shocks given the data, model, and parameters. The Kalman filter only works for linear problems, whereas the inversion filter (`:inversion`) works for linear and nonlinear models. If a nonlinear solution algorithm is selected, the inversion filter is used.
  * `data_in_levels` [Default: `true`, Type: `Bool`]: indicator whether the data is provided in levels. If `true` the input to the data argument will have the non stochastic steady state substracted.
  * `levels` [Default: `true`, Type: `Bool`]: return levels or absolute deviations from the relevant steady state corresponding to the solution algorithm (e.g. stochastic steady state for higher order solution algorithms).
  * `smooth` [Default: `true`, Type: `Bool`]: whether to return smoothed (`true`) or filtered (`false`) shocks/variables. Only works for the Kalman filter. The inversion filter only returns filtered shocks/variables.
  * `quadratic_matrix_equation_algorithm` [Default: `:schur`, Type: `Symbol`]: algorithm to solve quadratic matrix equation (`A * X ^ 2 + B * X + C = 0`). Available algorithms: `:schur`, `:doubling`
  * `sylvester_algorithm` [Default: function of size of problem, with smaller problems: `:doubling`, and larger problems: `:bicgstab`, Type: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: algorithm to solve Sylvester equation (`A * X * B + C = X`). Available algorithms: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`. Input argument can be up to two elements in a `Vector` or `Tuple`. The first (second) element corresponds to the second (third) order perturbation solutions' Sylvester equation. If only one element is provided it corresponds to the second order perturbation solutions' Sylvester equation.
  * `lyapunov_algorithm` [Default: `:doubling`, Type: `Symbol`]: algorithm to solve Lyapunov equation (`A * X * A' + C = X`). Available algorithms: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `tol` [Default: `Tolerances()`, Type: `Tolerances`]: define various tolerances for the algorithm used to solve the model. See documentation of [`Tolerances`](@ref) for more details: `?Tolerances`
  * `verbose` [Default: `false`, Type: `Bool`]: print information about results of the different solvers used to solve the model (non stochastic steady state solver, Sylvester equations, Lyapunov equation, and quadratic matrix equation).

# Returns

  * `KeyedArray` with variables in rows, and periods in columns.

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

simulation = simulate(RBC)

get_estimated_variables(RBC,simulation([:c],:,:simulate))
# output
2-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Variables ∈ 4-element Vector{Symbol}
→   Periods ∈ 40-element UnitRange{Int64}
And data, 4×40 Matrix{Float64}:
        (1)           (2)           (3)           (4)          …  (37)          (38)            (39)           (40)
  (:c)    5.92901       5.92797       5.92847       5.92048          5.95845       5.95697         5.95686        5.96173
  (:k)   47.3185       47.3087       47.3125       47.2392          47.6034       47.5969         47.5954        47.6402
  (:q)    6.87159       6.86452       6.87844       6.79352          7.00476       6.9026          6.90727        6.95841
  (:z)   -0.00109471   -0.00208056    4.43613e-5   -0.0123318        0.0162992     0.000445065     0.00119089     0.00863586
```
