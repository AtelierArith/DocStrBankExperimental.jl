```julia
get_estimated_variable_standard_deviations(
    𝓂,
    data;
    parameters,
    data_in_levels,
    smooth,
    verbose,
    tol,
    quadratic_matrix_equation_algorithm,
    lyapunov_algorithm
)

```

Return the standard deviations of the Kalman smoother or filter (depending on the `smooth` keyword argument) estimates of the model variables based on the provided data and first order solution of the model. Data is by default assumed to be in levels unless `data_in_levels` is set to `false`.

If occasionally binding constraints are present in the model, they are not taken into account here. 

# Arguments

  * `𝓂`: object created by [`@model`](@ref) and [`@parameters`](@ref).
  * `data` [Type: `KeyedArray`]: data matrix with variables (`String` or `Symbol`) in rows and time in columns

# Keyword Arguments

  * `parameters` [Default: `nothing`]: If `nothing` is provided, the solution is calculated for the parameters defined previously. Acceptable inputs are a `Vector` of parameter values, a `Vector` or `Tuple` of `Pair`s of the parameter `Symbol` or `String` and value. If the new parameter values differ from the previously defined the solution will be recalculated.
  * `data_in_levels` [Default: `true`, Type: `Bool`]: indicator whether the data is provided in levels. If `true` the input to the data argument will have the non stochastic steady state substracted.
  * `smooth` [Default: `true`, Type: `Bool`]: whether to return smoothed (`true`) or filtered (`false`) shocks/variables. Only works for the Kalman filter. The inversion filter only returns filtered shocks/variables.
  * `quadratic_matrix_equation_algorithm` [Default: `:schur`, Type: `Symbol`]: algorithm to solve quadratic matrix equation (`A * X ^ 2 + B * X + C = 0`). Available algorithms: `:schur`, `:doubling`
  * `lyapunov_algorithm` [Default: `:doubling`, Type: `Symbol`]: algorithm to solve Lyapunov equation (`A * X * A' + C = X`). Available algorithms: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `tol` [Default: `Tolerances()`, Type: `Tolerances`]: define various tolerances for the algorithm used to solve the model. See documentation of [`Tolerances`](@ref) for more details: `?Tolerances`
  * `verbose` [Default: `false`, Type: `Bool`]: print information about results of the different solvers used to solve the model (non stochastic steady state solver, Sylvester equations, Lyapunov equation, and quadratic matrix equation).

# Returns

  * `KeyedArray` with standard deviations in rows, and periods in columns.

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

get_estimated_variable_standard_deviations(RBC,simulation([:c],:,:simulate))
# output
2-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Standard_deviations ∈ 4-element Vector{Symbol}
→   Periods ∈ 40-element UnitRange{Int64}
And data, 4×40 Matrix{Float64}:
        (1)           (2)            (3)            (4)            …  (38)            (39)            (40)
  (:c)    1.23202e-9    1.84069e-10    8.23181e-11    8.23181e-11        8.23181e-11     8.23181e-11     0.0
  (:k)    0.00509299    0.000382934    2.87922e-5     2.16484e-6         1.6131e-9       9.31323e-10     1.47255e-9
  (:q)    0.0612887     0.0046082      0.000346483    2.60515e-5         1.31709e-9      1.31709e-9      9.31323e-10
  (:z)    0.00961766    0.000723136    5.43714e-5     4.0881e-6          3.08006e-10     3.29272e-10     2.32831e-10
```
