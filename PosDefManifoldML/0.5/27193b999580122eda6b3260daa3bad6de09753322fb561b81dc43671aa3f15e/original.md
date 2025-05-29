```julia
mutable struct ENLR <: ENLRmodel
    metric      :: Metric = Fisher;
    alpha       :: Real = 1.0
    pipeline    :: Pipeline
    normalize	:: Union{Function, Tuple, Nothing}
    intercept   :: Bool
    meanISR     :: Union{Hermitian, Nothing, UniformScaling}
    vecRange    :: UnitRange
    featDim     :: Int
    # GLMNet Models
    path        :: GLMNet.GLMNetPath
    cvλ         :: GLMNet.GLMNetCrossValidation
    best        :: GLMNet.GLMNetPath
end
```

ENLR machine learning models are incapsulated in this mutable structure. Fields:

`.metric`, of type [Metric](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#Metric::Enumerated-type-1), is the metric that will be adopted to compute the mean used as base-point for tangent space projection. By default the Fisher metric is adopted. See [mdm.jl](@ref) for the available metrics. If the data used to train the model are not positive definite matrices, but Euclidean feature vectors, the `.metric` field has no use. In order to use metrics you need to install the *PosDefManifold* package.

`.alpha` is the hyperparameter in $[0, 1]$ trading-off the **elestic-net model**. *α=0* requests a pure **ridge** model and *α=1* a pure **lasso** model. By default, *α=1* is specified (lasso model). This argument is usually passed as parameter to the [`fit`](@ref) function, defaulting therein to *α=1* too. See the examples here below.

All other fields do not correspond to arguments passed upon creation of the model by the default creator. Instead, they are filled later when a model is created by the [`fit`](@ref) function:

The field `pipeline`, of type [`Pipeline`](@ref), holds an optional sequence of data pre-conditioners to be applied to the data.  The pipeline is learnt when a ML model is fitted - see [`fit`](@ref) -  and stored in the model. If the pipeline is fitted, it is  automatically applied to the data at each call of the [`predict`](@ref) function.    

For the content of fields `normalize`, `intercept`, `meanISR` and `vecRange`, please see the documentation of the [`fit`](@ref) function for the ENLR model.

if the data used to train the model are positive definite matrices, `.featDim` is the length of the vectorized tangent vectors. This is given by *n(n+1)÷2* (integer division), where *n* is the dimension of the original PD matrices on which the model is applied once they are mapped onto the tangent space. If feature vectors are used to train the model, `.featDim` is the length of these vectors. If for fitting the model you have provided an optional keyword argument `vecRange`, `.featDim` will be reduced accordingly.

`.path` is an instance of the following `GLMNetPath` structure of the [GLMNet.jl](https://github.com/JuliaStats/GLMNet.jl) package. It holds the regularization path that is created when the [`fit`](@ref) function is invoked with optional keyword parameter `fitType` = `:path` or = `:all`:

```julia
struct GLMNetPath{F<:Distribution}
    family::F                        # Binomial()
    a0::Vector{Float64}              # intercept values for each solution
    betas::CompressedPredictorMatrix # coefficient values for each solution
    null_dev::Float64                # Null deviance of the model
    dev_ratio::Vector{Float64}       # R^2 values for each solution
    lambda::Vector{Float64}          # lambda values for each solution
    npasses::Int                     # actual number of passes over the
                                     # data for all lamda values
end
```

`.cvλ` is an instance of the following `GLMNetCrossValidation` structure of the [GLMNet.jl](https://github.com/JuliaStats/GLMNet.jl) package. It holds information about the cross-validation used for estimating the optimal lambda hyperparameter by the [`fit`](@ref) function when this is invoked with optional keyword parameter `fitType` = `:best` (default) or = `:all`:

```julia
struct GLMNetCrossValidation
    path::GLMNetPath            # the cv path
    nfolds::Int                 # the number of folds for the cv
    lambda::Vector{Float64}     # lambda values for each solution
    meanloss::Vector{Float64}   # mean loss for each solution
    stdloss::Vector{Float64}    # standard deviation of the mean losses
end
```

`.best` is an instance of the `GLMNetPath` structure (see above). It holds the model with the optimal lambda parameter found by cross-validation that is created by default when the [`fit`](@ref) function is invoked.

**Examples**:

```julia
# Note: creating models with the default creator is possible,
# but not useful in general.

using PosDefManifoldML, PosDefManifold

# Create an empty lasso model
m = ENLR(Fisher)

# Since the Fisher metric is the default metric,
# this is equivalent to
m = ENLR()

# Create an empty ridge model using the logEuclidean metric
m = ENLR(logEuclidean; alpha=0)

# Empty models can be passed as first argument of the `fit` function
# to fit a model. For instance, this will fit a ridge model of the same
# kind of `m` and put the fitted model in `m1`:
m1 = fit(m, PTr, yTr)

# In general you don't need this machinery for fitting a model,
# since you can specify a model by creating one on the fly:
m2 = fit(ENLR(logEuclidean; alpha=0), PTr, yTr)

# which is equivalent to
m2 = fit(ENLR(logEuclidean), PTr, yTr; alpha=0)

# Note that, albeit model `m` has been created as a ridge model,
# you have passed `m` and overwritten the `alpha` hyperparameter.
# The metric, instead, cannot be overwritten.
```
