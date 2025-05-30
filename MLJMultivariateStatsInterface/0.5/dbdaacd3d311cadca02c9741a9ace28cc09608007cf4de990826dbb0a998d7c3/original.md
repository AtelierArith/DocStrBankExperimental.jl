```
BayesianSubspaceLDA
```

A model type for constructing a Bayesian subspace LDA model, based on [MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
BayesianSubspaceLDA = @load BayesianSubspaceLDA pkg=MultivariateStats
```

Do `model = BayesianSubspaceLDA()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `BayesianSubspaceLDA(normalize=...)`.

The Bayesian multiclass subspace linear discriminant analysis algorithm learns a projection matrix as described in [`SubspaceLDA`](@ref). The posterior class probability distribution is derived as in [`BayesianLDA`](@ref).

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

`outdim`: the ouput dimension, automatically set to `min(indim, nclasses-1)` if equal   to `0`. If a non-zero `outdim` is passed, then the actual output dimension used is   `min(rank, outdim)` where `rank` is the rank of the within-class covariance matrix.

  * `priors::Union{Nothing, UnivariateFinite{<:Any, <:Any, <:Any, <:Real}, Dict{<:Any, <:Real}} = nothing`: For use in prediction with Bayes rule. If `priors = nothing` then `priors` are estimated from the class proportions in the training data. Otherwise it requires a `Dict` or `UnivariateFinite` object specifying the classes with non-zero probabilities in the training target.

# Operations

  * `transform(mach, Xnew)`: Return a lower dimensional projection of the input `Xnew`, which should have the same scitype as `X` above.
  * `predict(mach, Xnew)`: Return predictions of the target given features `Xnew`, which should have same scitype as `X` above. Predictions are probabilistic but uncalibrated.
  * `predict_mode(mach, Xnew)`: Return the modes of the probabilistic predictions returned above.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `classes`: The classes seen during model fitting.
  * `projection_matrix`: The learned projection matrix, of size `(indim, outdim)`, where `indim` and `outdim` are the input and output dimensions respectively (See Report section below).
  * `priors`: The class priors for classification. As inferred from training target `y`, if not user-specified. A `UnivariateFinite` object with levels consistent with `levels(y)`.

# Report

The fields of `report(mach)` are:

  * `indim`: The dimension of the input space i.e the number of training features.
  * `outdim`: The dimension of the transformed space the model is projected to.
  * `mean`: The overall mean of the training data.
  * `nclasses`: The number of classes directly observed in the training data (which can be less than the total number of classes in the class pool).

`class_means`: The class-specific means of the training data. A matrix of size   `(indim, nclasses)` with the ith column being the class-mean of the ith class in   `classes` (See fitted params section above).

  * `class_weights`: The weights (class counts) of each class. A vector of length `nclasses` with the ith element being the class weight of the ith class in `classes`. (See fitted params section above.)
  * `explained_variance_ratio`: The ratio of explained variance to total variance. Each dimension corresponds to an eigenvalue.

# Examples

```
using MLJ

BayesianSubspaceLDA = @load BayesianSubspaceLDA pkg=MultivariateStats

X, y = @load_iris # a table and a vector

model = BayesianSubspaceLDA()
mach = machine(model, X, y) |> fit!

Xproj = transform(mach, X)
y_hat = predict(mach, X)
labels = predict_mode(mach, X)
```

See also [`LDA`](@ref), [`BayesianLDA`](@ref), [`SubspaceLDA`](@ref)
