```
fit!(
    model::StateSpaceModel;
    filter::KalmanFilter=default_filter(model),
    optimizer::Optimizer=Optimizer(Optim.LBFGS()),
    save_hyperparameter_distribution::Bool=true
)
```

Estimate the state-space model parameters via maximum likelihood. The resulting optimal hyperparameters and the corresponding log-likelihood are stored within the model. You can choose the desired filter method (`UnivariateKalmanFilter`, `ScalarKalmanFilter`, etc.) and the [Optim.jl](https://github.com/JuliaNLSolvers/Optim.jl) optimization algortihm. 

# Example

```jldoctest
julia> model = LocalLevel(rand(100))
LocalLevel

julia> fit!(model)
LocalLevel

julia> model = LocalLinearTrend(LinRange(1, 100, 100) + rand(100))
LocalLinearTrend

julia> fit!(model; optimizer = Optimizer(StateSpaceModels.Optim.NelderMead()))
LocalLinearTrend
```
