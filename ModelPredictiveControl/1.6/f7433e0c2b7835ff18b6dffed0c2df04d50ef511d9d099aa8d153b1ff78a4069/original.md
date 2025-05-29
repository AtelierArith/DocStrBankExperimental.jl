```
updatestate!(estim::StateEstimator, u, ym, d=[]) -> x̂next
```

Update `estim.x̂0` estimate with current inputs `u`, measured outputs `ym` and dist. `d`. 

This function should be called at the end of each discrete time step. It removes the  operating points with [`remove_op!`](@ref), calls [`update_estimate!`](@ref) and returns the state estimate for the next time step $\mathbf{x̂}_k(k+1)$. The method [`preparestate!`](@ref) should be called prior to this one to correct the estimate when applicable (if `estim.direct == true`). Note that the [`MovingHorizonEstimator`](@ref) with the default `direct=true` option is not able to estimate $\mathbf{x̂}_k(k+1)$, the returned value is therefore the current corrected state $\mathbf{x̂}_k(k)$.

# Examples

```jldoctest
julia> kf = SteadyKalmanFilter(LinModel(ss(0.1, 0.5, 1, 0, 4.0))); u = [1]; ym = [0];

julia> preparestate!(kf, ym);

julia> x̂ = updatestate!(kf, u, ym) # x̂[2] is the integrator state (nint_ym argument)
2-element Vector{Float64}:
 0.5
 0.0
```
