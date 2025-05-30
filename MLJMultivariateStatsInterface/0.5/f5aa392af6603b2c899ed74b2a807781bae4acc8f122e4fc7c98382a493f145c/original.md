```
BayesianLDA
```

A model type for constructing a Bayesian LDA model, based on [MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
BayesianLDA = @load BayesianLDA pkg=MultivariateStats
```

Do `model = BayesianLDA()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `BayesianLDA(method=...)`.

The Bayesian multiclass LDA algorithm learns a projection matrix as described in ordinary [`LDA`](@ref).  Predicted class posterior probability distributions are derived by applying Bayes' rule with a multivariate Gaussian class-conditional distribution. A prior class distribution can be specified by the user or inferred from training data class frequency.

See also the [package documentation](https://multivariatestatsjl.readthedocs.io/en/latest/lda.html).  For more information about the algorithm, see [Li, Zhu and Ogihara (2006): Using Discriminant Analysis for Multi-class Classification: An Experimental Investigation](https://doi.org/10.1007/s10115-006-0013-y).

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

  * `method::Symbol=:gevd`: choice of solver, one of `:gevd` or `:whiten` methods.
  * `cov_w::StatsBase.SimpleCovariance()`: An estimator for the within-class covariance (used in computing the within-class scatter matrix, `Sw`). Any robust estimator from `CovarianceEstimation.jl` can be used.
  * `cov_b::StatsBase.SimpleCovariance()`: The same as `cov_w` but for the between-class covariance (used in computing the between-class scatter matrix, `Sb`).
  * `outdim::Int=0`: The output dimension, i.e., dimension of the transformed space, automatically set to `min(indim, nclasses-1)` if equal to 0.
  * `regcoef::Float64=1e-6`: The regularization coefficient. A positive value `regcoef*eigmax(Sw)` where `Sw` is the within-class scatter matrix, is added to the diagonal of `Sw` to improve numerical stability. This can be useful if using the standard covariance estimator.
  * `priors::Union{Nothing, UnivariateFinite{<:Any, <:Any, <:Any, <:Real}, Dict{<:Any, <:Real}} = nothing`: For use in prediction with Bayes rule. If `priors = nothing` then `priors` are estimated from the class proportions in the training data. Otherwise it requires a `Dict` or `UnivariateFinite` object specifying the classes with non-zero probabilities in the training target.

# Operations

  * `transform(mach, Xnew)`: Return a lower dimensional projection of the input `Xnew`, which should have the same scitype as `X` above.
  * `predict(mach, Xnew)`: Return predictions of the target given features `Xnew`, which should have the same scitype as `X` above. Predictions are probabilistic but uncalibrated.
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
  * `mean`: The mean of the untransformed training data. A vector of length `indim`.
  * `nclasses`: The number of classes directly observed in the training data (which can be less than the total number of classes in the class pool).
  * `class_means`: The class-specific means of the training data. A matrix of size `(indim, nclasses)` with the ith column being the class-mean of the ith class in `classes` (See fitted params section above).
  * `class_weights`: The weights (class counts) of each class. A vector of length `nclasses` with the ith element being the class weight of the ith class in `classes`. (See fitted params section above.)
  * `Sb`: The between class scatter matrix.
  * `Sw`: The within class scatter matrix.

# Examples

```
using MLJ

BayesianLDA = @load BayesianLDA pkg=MultivariateStats

X, y = @load_iris # a table and a vector

model = BayesianLDA()
mach = machine(model, X, y) |> fit!

Xproj = transform(mach, X)
y_hat = predict(mach, X)
labels = predict_mode(mach, X)
```

See also [`LDA`](@ref), [`SubspaceLDA`](@ref), [`BayesianSubspaceLDA`](@ref)
