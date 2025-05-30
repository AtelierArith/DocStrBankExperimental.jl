```
LDA
```

A model type for constructing a linear discriminant analysis model, based on [MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
LDA = @load LDA pkg=MultivariateStats
```

Do `model = LDA()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `LDA(method=...)`.

[Multiclass linear discriminant analysis](https://en.wikipedia.org/wiki/Linear_discriminant_analysis) learns a projection in a space of features to a lower dimensional space, in a way that attempts to preserve as much as possible the degree to which the classes of a discrete target variable can be discriminated. This can be used either for dimension reduction of the features (see `transform` below) or for probabilistic classification of the target (see `predict` below).

In the case of prediction, the class probability for a new observation reflects the proximity of that observation to training observations associated with that class, and how far away the observation is from observations associated with other classes. Specifically, the distances, in the transformed (projected) space, of a new observation, from the centroid of each target class, is computed; the resulting vector of distances, multiplied by minus one, is passed to a softmax function to obtain a class probability prediction. Here "distance" is computed using a user-specified distance function.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X, y)
```

Here:

  * `X` is any table of input features (eg, a `DataFrame`) whose columns are of scitype `Continuous`; check column scitypes with `schema(X)`.
  * `y` is the target, which can be any `AbstractVector` whose element scitype is `OrderedFactor` or `Multiclass`; check the scitype with `scitype(y)`

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * `method::Symbol=:gevd`: The solver, one of `:gevd` or `:whiten` methods.
  * `cov_w::StatsBase.SimpleCovariance()`: An estimator for the within-class covariance (used in computing the within-class scatter matrix, `Sw`). Any robust estimator from `CovarianceEstimation.jl` can be used.
  * `cov_b::StatsBase.SimpleCovariance()`: The same as `cov_w` but for the between-class covariance (used in computing the between-class scatter matrix, `Sb`).
  * `outdim::Int=0`: The output dimension, i.e dimension of the transformed space, automatically set to `min(indim, nclasses-1)` if equal to 0.
  * `regcoef::Float64=1e-6`: The regularization coefficient. A positive value `regcoef*eigmax(Sw)` where `Sw` is the within-class scatter matrix, is added to the diagonal of `Sw` to improve numerical stability. This can be useful if using the standard covariance estimator.
  * `dist=Distances.SqEuclidean()`: The distance metric to use when performing classification (to compare the distance between a new point and centroids in the transformed space); must be a subtype of `Distances.SemiMetric` from Distances.jl, e.g., `Distances.CosineDist`.

# Operations

  * `transform(mach, Xnew)`: Return a lower dimensional projection of the input `Xnew`, which should have the same scitype as `X` above.
  * `predict(mach, Xnew)`: Return predictions of the target given features `Xnew` having the same scitype as `X` above. Predictions are probabilistic but uncalibrated.
  * `predict_mode(mach, Xnew)`: Return the modes of the probabilistic predictions returned above.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `classes`: The classes seen during model fitting.
  * `projection_matrix`: The learned projection matrix, of size `(indim, outdim)`, where `indim` and `outdim` are the input and output dimensions respectively (See Report section below).

# Report

The fields of `report(mach)` are:

  * `indim`: The dimension of the input space i.e the number of training features.
  * `outdim`: The dimension of the transformed space the model is projected to.
  * `mean`: The mean of the untransformed training data. A vector of length `indim`.
  * `nclasses`: The number of classes directly observed in the training data (which can be less than the total number of classes in the class pool).
  * `class_means`: The class-specific means of the training data. A matrix of size `(indim, nclasses)` with the ith column being the class-mean of the ith class in `classes` (See fitted params section above).
  * `class_weights`: The weights (class counts) of each class. A vector of length `nclasses` with the ith element being the class weight of the ith class in `classes`. (See fitted params section above.)
  * `Sb`: The between class scatter matrix.
  * `Sw`: The within class scatter matrix.

# Examples

```
using MLJ

LDA = @load LDA pkg=MultivariateStats

X, y = @load_iris # a table and a vector

model = LDA()
mach = machine(model, X, y) |> fit!

Xproj = transform(mach, X)
y_hat = predict(mach, X)
labels = predict_mode(mach, X)

```

See also [`BayesianLDA`](@ref), [`SubspaceLDA`](@ref), [`BayesianSubspaceLDA`](@ref)
