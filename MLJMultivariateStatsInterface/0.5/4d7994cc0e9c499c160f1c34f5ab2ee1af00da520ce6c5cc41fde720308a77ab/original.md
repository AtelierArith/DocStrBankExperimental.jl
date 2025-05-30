```
LinearRegressor
```

A model type for constructing a linear regressor, based on [MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
LinearRegressor = @load LinearRegressor pkg=MultivariateStats
```

Do `model = LinearRegressor()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `LinearRegressor(bias=...)`.

`LinearRegressor` assumes the target is a `Continuous` variable and trains a linear prediction function using the least squares algorithm. Options exist to specify a bias  term.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X, y)
```

Here:

  * `X` is any table of input features (eg, a `DataFrame`) whose columns are of scitype    `Continuous`; check the column scitypes with `schema(X)`.
  * `y` is the target, which can be any `AbstractVector` whose element scitype is    `Continuous`; check the scitype with `scitype(y)`.

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * `bias=true`: Include the bias term if true, otherwise fit without bias term.

# Operations

  * `predict(mach, Xnew)`: Return predictions of the target given new features `Xnew`, which    should have the same scitype as `X` above.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `coefficients`: The linear coefficients determined by the model.
  * `intercept`: The intercept determined by the model.

# Examples

```
using MLJ

LinearRegressor = @load LinearRegressor pkg=MultivariateStats
linear_regressor = LinearRegressor()

X, y = make_regression(100, 2) # a table and a vector (synthetic data)
mach = machine(linear_regressor, X, y) |> fit!

Xnew, _ = make_regression(3, 2)
yhat = predict(mach, Xnew) # new predictions
```

See also [`MultitargetLinearRegressor`](@ref), [`RidgeRegressor`](@ref), [`MultitargetRidgeRegressor`](@ref)
