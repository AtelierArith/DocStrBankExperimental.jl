```
evaloutput(estim::StateEstimator, d=[]) -> ŷ
```

Evaluate `StateEstimator` outputs `ŷ` from `estim.x̂0` states and disturbances `d`.

It returns `estim` output at the current time step $\mathbf{ŷ}(k)$. If `estim.direct` is `true`, the method [`preparestate!`](@ref) should be called beforehand to correct the state estimate. 

Calling a [`StateEstimator`](@ref) object calls this `evaloutput` method.

# Examples

```jldoctest
julia> kf = SteadyKalmanFilter(setop!(LinModel(tf(2, [10, 1]), 5), yop=[20]), direct=false);

julia> ŷ = evaloutput(kf)
1-element Vector{Float64}:
 20.0
```
