```
ElasticNetRegressor
```

A model type for constructing a elastic net regressor, based on [MLJLinearModels.jl](https://github.com/alan-turing-institute/MLJLinearModels.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
ElasticNetRegressor = @load ElasticNetRegressor pkg=MLJLinearModels
```

Do `model = ElasticNetRegressor()` to construct an instance with default hyper-parameters.

Elastic net is a linear model with objective function

$|Xθ - y|₂²/2 + n⋅λ|θ|₂²/2 + n⋅γ|θ|₁$

where $n$ is the number of observations.

If  `scale_penalty_with_samples = false` the objective function is instead

$|Xθ - y|₂²/2 + λ|θ|₂²/2 + γ|θ|₁$.

Different solver options exist, as indicated under "Hyperparameters" below. 

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X, y)
```

where:

  * `X` is any table of input features (eg, a `DataFrame`) whose columns have `Continuous` scitype; check column scitypes with `schema(X)`
  * `y` is the target, which can be any `AbstractVector` whose element scitype is `Continuous`; check the scitype with `scitype(y)`

Train the machine using `fit!(mach, rows=...)`.

# Hyperparameters

  * `lambda::Real`: strength of the L2 regularization. Default: 1.0
  * `gamma::Real`: strength of the L1 regularization. Default: 0.0
  * `fit_intercept::Bool`: whether to fit the intercept or not. Default: true
  * `penalize_intercept::Bool`: whether to penalize the intercept. Default: false
  * `scale_penalty_with_samples::Bool`: whether to scale the penalty with the number of observations. Default: true
  * `solver::Union{Nothing, MLJLinearModels.Solver}`: any instance of `MLJLinearModels.ProxGrad`.

    If `solver=nothing` (default) then `ProxGrad(accel=true)` (FISTA) is used.

    Solver aliases: `FISTA(; kwargs...) = ProxGrad(accel=true, kwargs...)`, `ISTA(; kwargs...) = ProxGrad(accel=false, kwargs...)`.  Default: nothing

## Example

```
using MLJ
X, y = make_regression()
mach = fit!(machine(ElasticNetRegressor(), X, y))
predict(mach, X)
fitted_params(mach)
```

See also [`LassoRegressor`](@ref).
