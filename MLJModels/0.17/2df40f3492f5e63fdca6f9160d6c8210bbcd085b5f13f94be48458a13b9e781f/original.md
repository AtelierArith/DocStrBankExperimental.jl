```
ConstantClassifier
```

This "dummy" probabilistic predictor always returns the same distribution, irrespective of the provided input pattern. The distribution `d` returned is the `UnivariateFinite` distribution based on frequency of classes observed in the training target data. So, `pdf(d, level)` is the number of times the training target takes on the value `level`. Use `predict_mode` instead of `predict` to obtain the training target mode instead. For more on the `UnivariateFinite` type, see the CategoricalDistributions.jl package.

Almost any reasonable model is expected to outperform `ConstantClassifier`, which is used almost exclusively for testing and establishing performance baselines.

In MLJ (or MLJModels) do `model = ConstantClassifier()` to construct an instance.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X, y)
```

Here:

  * `X` is any table of input features (eg, a `DataFrame`)
  * `y` is the target, which can be any `AbstractVector` whose element scitype is `Finite`; check the scitype with `schema(y)`

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

None.

# Operations

  * `predict(mach, Xnew)`: Return predictions of the target given features `Xnew` (which for this model are ignored). Predictions are probabilistic.
  * `predict_mode(mach, Xnew)`: Return the mode of the probabilistic predictions returned above.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `target_distribution`: The distribution fit to the supplied target data.

# Examples

```julia
using MLJ

clf = ConstantClassifier()

X, y = @load_crabs # a table and a categorical vector
mach = machine(clf, X, y) |> fit!

fitted_params(mach)

Xnew = (;FL = [8.1, 24.8, 7.2],
        RW = [5.1, 25.7, 6.4],
        CL = [15.9, 46.7, 14.3],
        CW = [18.7, 59.7, 12.2],
        BD = [6.2, 23.6, 8.4],)

# probabilistic predictions:
yhat = predict(mach, Xnew)
yhat[1]

# raw probabilities:
pdf.(yhat, "B")

# probability matrix:
L = levels(y)
pdf(yhat, L)

# point predictions:
predict_mode(mach, Xnew)
```

See also [`ConstantRegressor`](@ref)
