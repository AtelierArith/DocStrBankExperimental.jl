```
preparestate!(estim::StateEstimator, ym, d=[]) -> x̂
```

Prepare `estim.x̂0` estimate with meas. outputs `ym` and dist. `d` for the current time step.

This function should be called at the beginning of each discrete time step. Its behavior depends if `estim` is a [`StateEstimator`](@ref) in the current/filter (1.) or  delayed/predictor (2.) formulation:

1. If `estim.direct` is `true`, it removes the operating points with [`remove_op!`](@ref), calls [`correct_estimate!`](@ref), and returns the corrected state estimate  $\mathbf{x̂}_k(k)$.
2. Else, it does nothing and returns the current best estimate $\mathbf{x̂}_{k-1}(k)$.

# Examples

```jldoctest
julia> estim2 = SteadyKalmanFilter(LinModel(ss(0.1, 0.5, 1, 0, 4)), nint_ym=0, direct=true);

julia> x̂ = round.(preparestate!(estim2, [1]), digits=3)
1-element Vector{Float64}:
 0.01

julia> estim1 = SteadyKalmanFilter(LinModel(ss(0.1, 0.5, 1, 0, 4)), nint_ym=0, direct=false);

julia> x̂ = preparestate!(estim1, [1])
1-element Vector{Float64}:
 0.0
```
