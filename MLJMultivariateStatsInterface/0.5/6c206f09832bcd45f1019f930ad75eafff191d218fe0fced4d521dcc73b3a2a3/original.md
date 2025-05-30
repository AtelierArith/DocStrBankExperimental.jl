```
MultitargetLinearRegressor
```

A model type for constructing a multitarget linear regressor, based on [MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
MultitargetLinearRegressor = @load MultitargetLinearRegressor pkg=MultivariateStats
```

Do `model = MultitargetLinearRegressor()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `MultitargetLinearRegressor(bias=...)`.

`MultitargetLinearRegressor` assumes the target variable is vector-valued with continuous components.  It trains a linear prediction function using the least squares algorithm. Options exist to specify a bias term.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X, y)
```

Here:

  * `X` is any table of input features (eg, a `DataFrame`) whose columns are of scitype    `Continuous`; check column scitypes with `schema(X)`.
  * `y` is the target, which can be any table of responses whose element scitype is    `Continuous`; check the scitype with `scitype(y)`.

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * `bias=true`: Include the bias term if true, otherwise fit without bias term.

# Operations

  * `predict(mach, Xnew)`: Return predictions of the target given new features `Xnew`,    which should have the same scitype as `X` above.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `coefficients`: The linear coefficients determined by the model.
  * `intercept`: The intercept determined by the model.

# Examples

```
using MLJ
using DataFrames

LinearRegressor = @load MultitargetLinearRegressor pkg=MultivariateStats
linear_regressor = LinearRegressor()

X, y = make_regression(100, 9; n_targets = 2) # a table and a table (synthetic data)

mach = machine(linear_regressor, X, y) |> fit!

Xnew, _ = make_regression(3, 9)
yhat = predict(mach, Xnew) # new predictions
```

See also [`LinearRegressor`](@ref), [`RidgeRegressor`](@ref), [`MultitargetRidgeRegressor`](@ref)
