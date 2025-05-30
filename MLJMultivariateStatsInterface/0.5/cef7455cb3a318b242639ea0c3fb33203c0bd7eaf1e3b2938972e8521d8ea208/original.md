```
RidgeRegressor
```

A model type for constructing a ridge regressor, based on [MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
RidgeRegressor = @load RidgeRegressor pkg=MultivariateStats
```

Do `model = RidgeRegressor()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `RidgeRegressor(lambda=...)`.

`RidgeRegressor` adds a quadratic penalty term to least squares regression, for regularization. Ridge regression is particularly useful in the case of multicollinearity. Options exist to specify a bias term, and to adjust the strength of the penalty term.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X, y)
```

Here:

  * `X` is any table of input features (eg, a `DataFrame`) whose columns are of scitype    `Continuous`; check column scitypes with `schema(X)`.
  * `y` is the target, which can be any `AbstractVector` whose element scitype is    `Continuous`; check the scitype with `scitype(y)`

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * `lambda=1.0`: Is the non-negative parameter for the regularization strength. If lambda    is 0, ridge regression is equivalent to linear least squares regression, and as lambda    approaches infinity, all the linear coefficients approach 0.
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

RidgeRegressor = @load RidgeRegressor pkg=MultivariateStats
pipe = Standardizer() |> RidgeRegressor(lambda=10)

X, y = @load_boston

mach = machine(pipe, X, y) |> fit!
yhat = predict(mach, X)
training_error = l1(yhat, y) |> mean
```

See also [`LinearRegressor`](@ref), [`MultitargetLinearRegressor`](@ref), [`MultitargetRidgeRegressor`](@ref)
