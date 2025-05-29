```
LADRegressor
```

A model type for constructing a lad regressor, based on [MLJLinearModels.jl](https://github.com/alan-turing-institute/MLJLinearModels.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
LADRegressor = @load LADRegressor pkg=MLJLinearModels
```

Do `model = LADRegressor()` to construct an instance with default hyper-parameters.

Least absolute deviation regression is a linear model with objective function

$∑ρ(Xθ - y) + n⋅λ|θ|₂² + n⋅γ|θ|₁$

where $ρ$ is the absolute loss and $n$ is the number of observations.

If `scale_penalty_with_samples = false` the objective function is instead

$∑ρ(Xθ - y) + λ|θ|₂² + γ|θ|₁$.

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

See also `RobustRegressor`.

## Parameters

  * `lambda::Real`: strength of the regularizer if `penalty` is `:l2` or `:l1`.     Strength of the L2 regularizer if `penalty` is `:en`. Default: 1.0
  * `gamma::Real`: strength of the L1 regularizer if `penalty` is `:en`. Default: 0.0
  * `penalty::Union{String, Symbol}`: the penalty to use, either `:l2`, `:l1`, `:en` (elastic net) or `:none`. Default: :l2
  * `fit_intercept::Bool`: whether to fit the intercept or not. Default: true
  * `penalize_intercept::Bool`: whether to penalize the intercept. Default: false
  * `scale_penalty_with_samples::Bool`: whether to scale the penalty with the number of observations. Default: true
  * `solver::Union{Nothing, MLJLinearModels.Solver}`: some instance of `MLJLinearModels.S` where `S` is one of: `LBFGS`, `IWLSCG`, if `penalty = :l2`, and `ProxGrad` otherwise.

    If `solver = nothing` (default) then `LBFGS()` is used, if `penalty = :l2`, and otherwise `ProxGrad(accel=true)` (FISTA) is used.

    Solver aliases: `FISTA(; kwargs...) = ProxGrad(accel=true, kwargs...)`, `ISTA(; kwargs...) = ProxGrad(accel=false, kwargs...)` Default: nothing

## Example

```
using MLJ
X, y = make_regression()
mach = fit!(machine(LADRegressor(), X, y))
predict(mach, X)
fitted_params(mach)
```
