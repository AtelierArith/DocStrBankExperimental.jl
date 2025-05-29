```
ConstantRegressor
```

This "dummy" probabilistic predictor always returns the same distribution, irrespective of the provided input pattern. The distribution returned is the one of the type specified that best fits the training target data. Use `predict_mean` or `predict_median` to predict the mean or median values instead. If not specified, a normal distribution is fit.

Almost any reasonable model is expected to outperform `ConstantRegressor` which is used almost exclusively for testing and establishing performance baselines.

In MLJ (or MLJModels) do `model = ConstantRegressor()` or `model = ConstantRegressor(distribution=...)` to construct a model instance.

# Training data

In MLJ (or MLJBase) bind an instance `model` to data with

```
mach = machine(model, X, y)
```

Here:

  * `X` is any table of input features (eg, a `DataFrame`)
  * `y` is the target, which can be any `AbstractVector` whose element scitype is `Continuous`; check the scitype with `schema(y)`

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * `distribution_type=Distributions.Normal`: The distribution to be fit to the target data. Must be a subtype of `Distributions.ContinuousUnivariateDistribution`.

# Operations

  * `predict(mach, Xnew)`: Return predictions of the target given features `Xnew` (which for this model are ignored). Predictions are probabilistic.
  * `predict_mean(mach, Xnew)`: Return instead the means of the probabilistic predictions returned above.
  * `predict_median(mach, Xnew)`: Return instead the medians of the probabilistic predictions returned above.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `target_distribution`: The distribution fit to the supplied target data.

# Examples

```julia
using MLJ

X, y = make_regression(10, 2) # synthetic data: a table and vector
regressor = ConstantRegressor()
mach = machine(regressor, X, y) |> fit!

fitted_params(mach)

Xnew, _ = make_regression(3, 2)
predict(mach, Xnew)
predict_mean(mach, Xnew)

```

See also [`ConstantClassifier`](@ref)
