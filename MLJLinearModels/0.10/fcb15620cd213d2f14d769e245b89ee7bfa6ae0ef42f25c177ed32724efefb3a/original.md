```
LinearRegressor
```

A model type for constructing a linear regressor, based on [MLJLinearModels.jl](https://github.com/alan-turing-institute/MLJLinearModels.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
LinearRegressor = @load LinearRegressor pkg=MLJLinearModels
```

Do `model = LinearRegressor()` to construct an instance with default hyper-parameters.

This model provides standard linear regression with objective function

$|Xθ - y|₂²/2$

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

  * `fit_intercept::Bool`: whether to fit the intercept or not. Default: true
  * `solver::Union{Nothing, MLJLinearModels.Solver}`: "any instance of `MLJLinearModels.Analytical`. Use `Analytical()` for Cholesky and `CG()=Analytical(iterative=true)` for conjugate-gradient.

    If `solver = nothing` (default) then `Analytical()` is used.  Default: nothing

## Example

```
using MLJ
X, y = make_regression()
mach = fit!(machine(LinearRegressor(), X, y))
predict(mach, X)
fitted_params(mach)
```
