```
SubspaceLDA
```

A model type for constructing a subpace LDA model, based on [MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
SubspaceLDA = @load SubspaceLDA pkg=MultivariateStats
```

Do `model = SubspaceLDA()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `SubspaceLDA(normalize=...)`.

Multiclass subspace linear discriminant analysis (LDA) is a variation on ordinary [`LDA`](@ref) suitable for high dimensional data, as it avoids storing scatter matrices. For details, refer the [MultivariateStats.jl documentation](https://juliastats.org/MultivariateStats.jl/stable/).

In addition to dimension reduction (using `transform`) probabilistic classification is provided (using `predict`).  In the case of classification, the class probability for a new observation reflects the proximity of that observation to training observations associated with that class, and how far away the observation is from observations associated with other classes. Specifically, the distances, in the transformed (projected) space, of a new observation, from the centroid of each target class, is computed; the resulting vector of distances, multiplied by minus one, is passed to a softmax function to obtain a class probability prediction. Here "distance" is computed using a user-specified distance function.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X, y)
```

Here:

  * `X` is any table of input features (eg, a `DataFrame`) whose columns are of scitype `Continuous`; check column scitypes with `schema(X)`.
  * `y` is the target, which can be any `AbstractVector` whose element scitype is `OrderedFactor` or `Multiclass`; check the scitype with `scitype(y)`.

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * `normalize=true`: Option to normalize the between class variance for the number of observations in each class, one of `true` or `false`.
  * `outdim`: the ouput dimension, automatically set to `min(indim, nclasses-1)` if equal to `0`. If a non-zero `outdim` is passed, then the actual output dimension used is `min(rank, outdim)` where `rank` is the rank of the within-class covariance matrix.
  * `dist=Distances.SqEuclidean()`: The distance metric to use when performing classification (to compare the distance between a new point and centroids in the transformed space); must be a subtype of `Distances.SemiMetric` from Distances.jl, e.g., `Distances.CosineDist`.

# Operations

  * `transform(mach, Xnew)`: Return a lower dimensional projection of the input `Xnew`, which should have the same scitype as `X` above.
  * `predict(mach, Xnew)`: Return predictions of the target given features `Xnew`, which should have same scitype as `X` above. Predictions are probabilistic but uncalibrated.
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
  * `nclasses`: The number of classes directly observed in the training data (which can be less than the total number of classes in the class pool)

`class_means`: The class-specific means of the training data. A matrix of size   `(indim, nclasses)` with the ith column being the class-mean of the ith class in   `classes` (See fitted params section above).

  * `class_weights`: The weights (class counts) of each class. A vector of length `nclasses` with the ith element being the class weight of the ith class in `classes`. (See fitted params section above.)
  * `explained_variance_ratio`: The ratio of explained variance to total variance. Each dimension corresponds to an eigenvalue.

# Examples

```
using MLJ

SubspaceLDA = @load SubspaceLDA pkg=MultivariateStats

X, y = @load_iris # a table and a vector

model = SubspaceLDA()
mach = machine(model, X, y) |> fit!

Xproj = transform(mach, X)
y_hat = predict(mach, X)
labels = predict_mode(mach, X)
```

See also [`LDA`](@ref), [`BayesianLDA`](@ref), [`BayesianSubspaceLDA`](@ref)
