```
SimResult(obj::SimModel,             U_data, Y_data, D_data=[]; <keyword arguments>)
SimResult(obj::StateEstimator,       U_data, Y_data, D_data=[]; <keyword arguments>)
SimResult(obj::PredictiveController, U_data, Y_data, D_data=[]; <keyword arguments>)
```

Manually construct a `SimResult` to quickly plot `obj` simulations.

Except for `obj`, all the arguments should be matrices of `N` columns, where `N` is the  number of time steps. [`SimResult`](@ref) objects allow to quickly plot simulation results. Simply call `plot` on them.

# Arguments

!!! info
    Keyword arguments with *`emphasis`* are non-Unicode alternatives.


  * `obj` : simulated [`SimModel`](@ref)/[`StateEstimator`](@ref)/[`PredictiveController`](@ref)
  * `U_data` : manipulated inputs
  * `Y_data` : plant outputs
  * `D_data=[]` : measured disturbances
  * `X_data=nothing` : plant states
  * `X̂_data=nothing` or *`Xhat_data`* : estimated states
  * `Ŷ_data=nothing` or *`Yhat_data`* : estimated outputs
  * `Ry_data=nothing` : plant output setpoints
  * `Ru_data=nothing` : manipulated input setpoints
  * `plant=get_model(obj)` : simulated plant model, default to `obj` internal plant model

# Examples

```jldoctest
julia> model = LinModel(tf(1, [1, 1]), 1.0);

julia> N = 5; U_data = fill(1.0, 1, N); Y_data = zeros(1, N);

julia> for i=1:N; updatestate!(model, U_data[:, i]); Y_data[:, i] = model(); end; Y_data
1×5 Matrix{Float64}:
 0.632121  0.864665  0.950213  0.981684  0.993262

julia> res = SimResult(model, U_data, Y_data)
Simulation results of LinModel with 5 time steps.
```
