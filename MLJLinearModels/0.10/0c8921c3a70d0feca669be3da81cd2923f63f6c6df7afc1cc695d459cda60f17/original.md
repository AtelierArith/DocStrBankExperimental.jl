```
MultinomialClassifier
```

A model type for constructing a multinomial classifier, based on [MLJLinearModels.jl](https://github.com/alan-turing-institute/MLJLinearModels.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
MultinomialClassifier = @load MultinomialClassifier pkg=MLJLinearModels
```

Do `model = MultinomialClassifier()` to construct an instance with default hyper-parameters.

This model coincides with [`LogisticClassifier`](@ref), except certain optimizations possible in the special binary case will not be applied. Its hyperparameters are identical.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X, y)
```

where:

  * `X` is any table of input features (eg, a `DataFrame`) whose columns have `Continuous` scitype; check column scitypes with `schema(X)`
  * `y` is the target, which can be any `AbstractVector` whose element scitype is `<:OrderedFactor` or `<:Multiclass`; check the scitype with `scitype(y)`

Train the machine using `fit!(mach, rows=...)`.

# Hyperparameters

  * `lambda::Real`: strength of the regularizer if `penalty` is `:l2` or `:l1`.     Strength of the L2 regularizer if `penalty` is `:en`. Default: eps()
  * `gamma::Real`: strength of the L1 regularizer if `penalty` is `:en`. Default: 0.0
  * `penalty::Union{String, Symbol}`: the penalty to use, either `:l2`, `:l1`, `:en` (elastic net) or `:none`. Default: :l2
  * `fit_intercept::Bool`: whether to fit the intercept or not. Default: true
  * `penalize_intercept::Bool`: whether to penalize the intercept. Default: false
  * `scale_penalty_with_samples::Bool`: whether to scale the penalty with the number of samples. Default: true
  * `solver::Union{Nothing, MLJLinearModels.Solver}`: some instance of `MLJLinearModels.S` where `S` is one of: `LBFGS`, `NewtonCG`, `ProxGrad`; but subject to the following restrictions:

      * If `penalty = :l2`, `ProxGrad` is disallowed. Otherwise, `ProxGrad` is the only option.
      * Unless `scitype(y) <: Finite{2}` (binary target) `Newton` is disallowed.

    If `solver = nothing` (default) then `ProxGrad(accel=true)` (FISTA) is used, unless `gamma = 0`, in which case `LBFGS()` is used.

    Solver aliases: `FISTA(; kwargs...) = ProxGrad(accel=true, kwargs...)`, `ISTA(; kwargs...) = ProxGrad(accel=false, kwargs...)` Default: nothing

## Example

```
using MLJ
X, y = make_blobs(centers = 3)
mach = fit!(machine(MultinomialClassifier(), X, y))
predict(mach, X)
fitted_params(mach)
```

See also [`LogisticClassifier`](@ref).
