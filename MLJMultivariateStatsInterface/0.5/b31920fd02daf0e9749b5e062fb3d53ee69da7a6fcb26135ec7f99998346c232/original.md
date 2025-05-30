```
MultitargetRidgeRegressor
```

A model type for constructing a multitarget ridge regressor, based on [MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
MultitargetRidgeRegressor = @load MultitargetRidgeRegressor pkg=MultivariateStats
```

Do `model = MultitargetRidgeRegressor()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `MultitargetRidgeRegressor(lambda=...)`.

Multi-target ridge regression adds a quadratic penalty term to multi-target least squares regression, for regularization. Ridge regression is particularly useful in the case of multicollinearity. In this case, the output represents a response vector. Options exist to specify a bias term, and to adjust the strength of the penalty term.

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
using DataFrames

RidgeRegressor = @load MultitargetRidgeRegressor pkg=MultivariateStats

X, y = make_regression(100, 6; n_targets = 2)  # a table and a table (synthetic data)

ridge_regressor = RidgeRegressor(lambda=1.5)
mach = machine(ridge_regressor, X, y) |> fit!

Xnew, _ = make_regression(3, 6)
yhat = predict(mach, Xnew) # new predictions
```

See also [`LinearRegressor`](@ref), [`MultitargetLinearRegressor`](@ref), [`RidgeRegressor`](@ref)
