```julia
get_conditional_forecast(
    𝓂,
    conditions;
    shocks,
    initial_state,
    periods,
    parameters,
    variables,
    conditions_in_levels,
    algorithm,
    levels,
    verbose,
    tol,
    quadratic_matrix_equation_algorithm,
    sylvester_algorithm,
    lyapunov_algorithm
)

```

Return the conditional forecast given restrictions on endogenous variables and shocks (optional). By default, the values represent absolute deviations from the relevant steady state (see `levels` for details). The non-stochastic steady state (NSSS) is relevant for first order solutions and the stochastic steady state for higher order solutions. A constrained minimisation problem is solved to find the combination of shocks with the smallest squared magnitude fulfilling the conditions.

If occasionally binding constraints are present in the model, they are not taken into account here. 

# Arguments

  * `𝓂`: object created by [`@model`](@ref) and [`@parameters`](@ref).
  * `conditions` [Type: `Union{Matrix{Union{Nothing,Float64}}, SparseMatrixCSC{Float64}, KeyedArray{Union{Nothing,Float64}}, KeyedArray{Float64}}`]: conditions for which to find the corresponding shocks. The input can have multiple formats, but for all types of entries the first dimension corresponds to variables and the second dimension to the number of periods. The conditions can be specified using a matrix of type `Matrix{Union{Nothing,Float64}}`. In this case the conditions are matrix elements of type `Float64` and all remaining (free) entries are `nothing`. You can also use a `SparseMatrixCSC{Float64}` as input. In this case only non-zero elements are taken as conditions. Note that you cannot condition variables to be zero using a `SparseMatrixCSC{Float64}` as input (use other input formats to do so). Another possibility to input conditions is by using a `KeyedArray`. You can use a `KeyedArray{Union{Nothing,Float64}}` where, similar to `Matrix{Union{Nothing,Float64}}`, all entries of type `Float64` are recognised as conditions and all other entries have to be `nothing`. Furthermore, you can specify in the primary axis a subset of variables (of type `Symbol` or `String`) for which you specify conditions and all other variables are considered free. The same goes for the case when you use `KeyedArray{Float64}}` as input, whereas in this case the conditions for the specified variables bind for all periods specified in the `KeyedArray`, because there are no `nothing` entries permitted with this type.

# Keyword Arguments

  * `shocks` [Default: `nothing`, Type: `Union{Matrix{Union{Nothing,Float64}}, SparseMatrixCSC{Float64}, KeyedArray{Union{Nothing,Float64}}, KeyedArray{Float64}, Nothing}`]: known values of shocks. This argument allows the user to include certain shock values. By entering restrictions on the shocks in this way the problem to match the conditions on endogenous variables is restricted to the remaining free shocks in the repective period. The input can have multiple formats, but for all types of entries the first dimension corresponds to shocks and the second dimension to the number of periods.  `shocks` can be specified using a matrix of type `Matrix{Union{Nothing,Float64}}`. In this case the shocks are matrix elements of type `Float64` and all remaining (free) entries are `nothing`. You can also use a `SparseMatrixCSC{Float64}` as input. In this case only non-zero elements are taken as certain shock values. Note that you cannot condition shocks to be zero using a `SparseMatrixCSC{Float64}` as input (use other input formats to do so). Another possibility to input known shocks is by using a `KeyedArray`. You can use a `KeyedArray{Union{Nothing,Float64}}` where, similar to `Matrix{Union{Nothing,Float64}}`, all entries of type `Float64` are recognised as known shocks and all other entries have to be `nothing`. Furthermore, you can specify in the primary axis a subset of shocks (of type `Symbol` or `String`) for which you specify values and all other shocks are considered free. The same goes for the case when you use `KeyedArray{Float64}}` as input, whereas in this case the values for the specified shocks bind for all periods specified in the `KeyedArray`, because there are no `nothing` entries permitted with this type.
  * `initial_state` [Default: `[0.0]`, Type: `Union{Vector{Vector{Float64}},Vector{Float64}}`]: The initial state defines the starting point for the model. In the case of pruned solution algorithms the initial state can be given as multiple state vectors (`Vector{Vector{Float64}}`). In this case the initial state must be given in deviations from the non-stochastic steady state. In all other cases the initial state must be given in levels. If a pruned solution algorithm is selected and `initial_state` is a `Vector{Float64}` then it impacts the first order initial state vector only. The state includes all variables as well as exogenous variables in leads or lags if present. `get_irf(𝓂, shocks = :none, variables = :all, periods = 1)` returns a `KeyedArray` with all variables.
  * `periods` [Default: `40`, Type: `Int`]: the total number of periods is the sum of the argument provided here and the maximum of periods of the shocks or conditions argument.
  * `parameters` [Default: `nothing`]: If `nothing` is provided, the solution is calculated for the parameters defined previously. Acceptable inputs are a `Vector` of parameter values, a `Vector` or `Tuple` of `Pair`s of the parameter `Symbol` or `String` and value. If the new parameter values differ from the previously defined the solution will be recalculated.
  * `variables` [Default: `:all_excluding_obc`]: variables for which to show the results. Inputs can be a variable name passed on as either a `Symbol` or `String` (e.g. `:y` or "y"), or `Tuple`, `Matrix` or `Vector` of `String` or `Symbol`. Any variables not part of the model will trigger a warning. `:all_excluding_auxilliary_and_obc` contains all shocks less those related to auxilliary variables and related to occasionally binding constraints (obc). `:all_excluding_obc` contains all shocks less those related to auxilliary variables. `:all` will contain all variables.
  * `conditions_in_levels` [Default: `true`, Type: `Bool`]: indicator whether the conditions are provided in levels. If `true` the input to the conditions argument will have the non-stochastic steady state substracted.
  * `levels` [Default: `false`, Type: `Bool`]: return levels or absolute deviations from the relevant steady state corresponding to the solution algorithm (e.g. stochastic steady state for higher order solution algorithms).
  * `algorithm` [Default: `:first_order`, Type: `Symbol`]: algorithm to solve for the dynamics of the model. Available algorithms: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `quadratic_matrix_equation_algorithm` [Default: `:schur`, Type: `Symbol`]: algorithm to solve quadratic matrix equation (`A * X ^ 2 + B * X + C = 0`). Available algorithms: `:schur`, `:doubling`
  * `sylvester_algorithm` [Default: function of size of problem, with smaller problems: `:doubling`, and larger problems: `:bicgstab`, Type: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: algorithm to solve Sylvester equation (`A * X * B + C = X`). Available algorithms: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`. Input argument can be up to two elements in a `Vector` or `Tuple`. The first (second) element corresponds to the second (third) order perturbation solutions' Sylvester equation. If only one element is provided it corresponds to the second order perturbation solutions' Sylvester equation.
  * `lyapunov_algorithm` [Default: `:doubling`, Type: `Symbol`]: algorithm to solve Lyapunov equation (`A * X * A' + C = X`). Available algorithms: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `tol` [Default: `Tolerances()`, Type: `Tolerances`]: define various tolerances for the algorithm used to solve the model. See documentation of [`Tolerances`](@ref) for more details: `?Tolerances`
  * `verbose` [Default: `false`, Type: `Bool`]: print information about results of the different solvers used to solve the model (non stochastic steady state solver, Sylvester equations, Lyapunov equation, and quadratic matrix equation).

# Returns

  * `KeyedArray` with variables  and shocks in rows, and periods in columns.

# Examples

```jldoctest
using MacroModelling
using SparseArrays, AxisKeys

@model RBC_CME begin
    y[0]=A[0]*k[-1]^alpha
    1/c[0]=beta*1/c[1]*(alpha*A[1]*k[0]^(alpha-1)+(1-delta))
    1/c[0]=beta*1/c[1]*(R[0]/Pi[+1])
    R[0] * beta =(Pi[0]/Pibar)^phi_pi
    A[0]*k[-1]^alpha=c[0]+k[0]-(1-delta*z_delta[0])*k[-1]
    z_delta[0] = 1 - rho_z_delta + rho_z_delta * z_delta[-1] + std_z_delta * delta_eps[x]
    A[0] = 1 - rhoz + rhoz * A[-1]  + std_eps * eps_z[x]
end

@parameters RBC_CME begin
    alpha = .157
    beta = .999
    delta = .0226
    Pibar = 1.0008
    phi_pi = 1.5
    rhoz = .9
    std_eps = .0068
    rho_z_delta = .9
    std_z_delta = .005
end

# c is conditioned to deviate by 0.01 in period 1 and y is conditioned to deviate by 0.02 in period 2
conditions = KeyedArray(Matrix{Union{Nothing,Float64}}(undef,2,2),Variables = [:c,:y], Periods = 1:2)
conditions[1,1] = .01
conditions[2,2] = .02

# in period 2 second shock (eps_z) is conditioned to take a value of 0.05
shocks = Matrix{Union{Nothing,Float64}}(undef,2,1)
shocks[1,1] = .05

get_conditional_forecast(RBC_CME, conditions, shocks = shocks, conditions_in_levels = false)
# output
2-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Variables_and_shocks ∈ 9-element Vector{Symbol}
→   Periods ∈ 42-element UnitRange{Int64}
And data, 9×42 Matrix{Float64}:
                (1)            (2)           …  (41)            (42)
  (:A)            0.0313639      0.0134792         0.000221372     0.000199235
  (:Pi)           0.000780257    0.00020929       -0.000146071    -0.000140137
  (:R)            0.00117156     0.00031425       -0.000219325    -0.000210417
  (:c)            0.01           0.00600605        0.00213278      0.00203751
  (:k)            0.034584       0.0477482   …     0.0397631       0.0380482
  (:y)            0.0446375      0.02              0.00129544      0.001222
  (:z_delta)      0.00025        0.000225          3.69522e-6      3.3257e-6
  (:delta_eps)    0.05           0.0               0.0             0.0
  (:eps_z)        4.61234       -2.16887           0.0             0.0

# The same can be achieved with the other input formats:
# conditions = Matrix{Union{Nothing,Float64}}(undef,7,2)
# conditions[4,1] = .01
# conditions[6,2] = .02

# using SparseArrays
# conditions = spzeros(7,2)
# conditions[4,1] = .01
# conditions[6,2] = .02

# shocks = KeyedArray(Matrix{Union{Nothing,Float64}}(undef,1,1),Variables = [:delta_eps], Periods = [1])
# shocks[1,1] = .05

# using SparseArrays
# shocks = spzeros(2,1)
# shocks[1,1] = .05
```
