```julia
function fit(model	:: ENLRmodel,
             𝐏Tr	 :: Union{HermitianVector, Matrix{Float64}},
             yTr	:: IntVector;

    # pipeline (data transformations)
    pipeline    :: Union{Pipeline, Nothing} = nothing,

    # parameters for projection onto the tangent space
    w           :: Union{Symbol, Tuple, Vector} = Float64[],
    meanISR     :: Union{Hermitian, Nothing, UniformScaling} = nothing,
    meanInit    :: Union{Hermitian, Nothing} = nothing,
    vecRange    :: UnitRange = 𝐏Tr isa ℍVector ? (1:size(𝐏Tr[1], 2)) : (1:size(𝐏Tr, 2)),
    normalize	:: Union{Function, Tuple, Nothing} = normalize!,

    # arguments for `GLMNet.glmnet` function
    alpha           :: Real = model.alpha,
    weights         :: Vector{Float64} = ones(Float64, length(yTr)),
    intercept       :: Bool = true,
    fitType         :: Symbol = :best,
    penalty_factor  :: Vector{Float64} = ones(Float64, _getDim(𝐏Tr, vecRange)),
    constraints     :: Matrix{Float64} = [x for x in (-Inf, Inf), y in 1:_getDim(𝐏Tr, vecRange)],
    offsets         :: Union{Vector{Float64}, Nothing} = nothing,
    dfmax           :: Int = _getDim(𝐏Tr, vecRange),
    pmax            :: Int = min(dfmax*2+20, _getDim(𝐏Tr, vecRange)),
    nlambda         :: Int = 100,
    lambda_min_ratio:: Real = (length(yTr)*2 < _getDim(𝐏Tr, vecRange) ? 1e-2 : 1e-4),
    lambda          :: Vector{Float64} = Float64[],
    maxit           :: Int = 1000000,
    algorithm       :: Symbol = :newtonraphson,
    checkArgs       :: Bool = true,

    # selection method
    λSelMeth        :: Symbol = :sd1,

    # arguments for `GLMNet.glmnetcv` function
    nfolds          :: Int = min(10, div(size(yTr, 1), 3)),
    folds           :: Vector{Int} =
    begin
        n, r = divrem(size(yTr, 1), nfolds)
        shuffle!([repeat(1:nfolds, outer=n); 1:r])
    end,
    parallel        :: Bool=true,

    # Generic and common parameters
    tol             :: Real = 1e-5,
    verbose         :: Bool = true,
    ⏩              :: Bool = true,
)
```

Create and fit an **2-class** elastic net logistic regression ([`ENLR`](@ref)) machine learning model, with training data `𝐏Tr`, of type [ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1), and corresponding labels `yTr`, of type [IntVector](@ref). Return the fitted model(s) as an instance of the [`ENLR`](@ref) structure.

!!! warning "Class Labels"
    Labels must be provided using the natural numbers, *i.e.*, `1` for the first class, `2` for the second class, etc.


As for all ML models acting in the tangent space, fitting an ENLR model involves computing a mean (barycenter) of all the matrices in `𝐏Tr`, projecting all matrices onto the tangent space after parallel transporting them at the identity matrix and vectorizing them using the [vecP](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.vecP) operation. Once this is done, the ENLR is fitted.

The mean is computed according to the `.metric` field of the `model`, with optional weights `w`. The `.metric` field of the `model` is passed internally to the [`tsMap`](@ref) function. By default the metric is the Fisher metric. See the examples here below to see how to change metric. See [mdm.jl](@ref) or check out directly the documentation of [PosDefManifold.jl](https://marco-congedo.github.io/PosDefManifold.jl/dev/) for the available metrics.

**Optional keyword arguments**

If a `pipeline`, of type [`Pipeline`](@ref) is provided,  all necessary parameters of the sequence of conditioners are fitted and all matrices  are transformed according to the specified pipeline before fitting the ML model. The parameters are stored in the output ML model. Note that the fitted pipeline is automatically applied by any successive call  to function [`predict`](@ref) to which the output ML model is passed as argument.

By default, uniform weights will be given to all observations for computing the mean to project the data in the tangent space. This is equivalent to passing as argument `w=:uniform` (or `w=:u`). You can also pass as argument:

  * `w=:balanced` (or simply `w=:b`). If the two classes are unbalanced, the weights should better be inversely proportional to the number of examples for each class, in such a way that each class contributes equally to the computation of the mean. This is equivalent of passing `w=tsWeights(yTr)`. See the [`tsWeights`](@ref) function for details.
  * `w=v`, where `v` is a user defined vector of non-negative weights for the observations, thus, `v` must contain the same number of elements as `yTr`. For example, `w=[1.0, 1.0, 2.0, 2.0, ...., 1.0]`
  * `w=t`, where `t` is a 2-tuple of real weights, one weight for each class, for example `w=(0.5, 1.5)`. This is equivalent to passing `w=tsWeights(yTr; classWeights=collect(0.5, 1.5))`, see the [`tsWeights`](@ref) function for details.

By default `meanISR=nothing` and the inverse square root (ISR) of the mean used for projecting the matrices onto the tangent space (see [`tsMap`](@ref)) is computed. An Hermitian matrix or `I` (the identity matrix) can also be passed  as argument `meanISR` and in this case this matrix will be used as the ISR of the mean. Passed or computed, it will be written in the `.meanISR` field of the  model structure created by this function. Notice that passing `I`, the matrices will be projected onto the tangent space at the identity without recentering them. This is possible if the matrices have been recentered bt a pre-conditioning pipeline (see [`Pipeline`](@ref)).

If `meanISR` is not provided and the `.metric` field of the `model` is Fisher, logdet0 or Wasserstein, the tolerance of the iterative algorithm used to compute the mean is set to argument `tol` (default 1e-5). Also, in this case a particular initialization for those iterative algorithms can be provided as an `Hermitian` matrix with argument `meanInit`.

!!! tip "Euclidean ENLR models"
    ML models acting on the tangent space allows to fit a model passing as training data `𝐏Tr` directly a matrix of feature vectors, where each feature vector is a row of the matrix. In this case none of the above keyword arguments are used.


**The following optional keyword arguments act on any kind of input, that is, tangent vectors and generic feature vectors**

If a `UnitRange` is passed with optional keyword argument `vecRange`, then if `𝐏Tr` is a vector of `Hermitian` matrices, the vectorization of those matrices once they are projected onto the tangent space concerns only the rows (or columns) given in the specified range, else if `𝐏Tr` is a matrix with feature vectors arranged in its rows, then only the columns of `𝐏Tr` given in the specified range will be used. Argument `vecRange` will be ignored if a pre-conditioning pipeline is used  and if the pipeline changes the dimension of the input matrices. In this case it will be set to its default value using the new dimension. You are not allowed to change this behavior.

With `normalize` the tangent (or feature) vectors can be normalized individually. Three functions can be passed, namely 

  * [`demean!`](@ref) to remove the mean,
  * [`normalize!`](@ref) to fix the norm (default),
  * [`standardize!`](@ref) to fix the mean to zero and the standard deviation to 1.

As argument `normalize` you can also pass a 2-tuple of real numbers. In this case the numbers will be the lower and upper limit to bound the vectors within these limits - see [`rescale!`](@ref).

!!! tip "Rescaling"
    If you wish to rescale, use `(-1, 1)`, since tangent vectors of SPD matrices have positive and negative elements. If `𝐏Tr` is a feature matrix and the features are only positive, use `(0, 1)` instead.


If you pass `nothing` as argument `normalize`, no normalization will be carried out.

The remaining optional keyword arguments, are

  * the arguments passed to the `GLMNet.glmnet` function for fitting the models. Those are always used.
  * the `λSelMeth` argument and the arguments passed to the `GLMNet.glmnetcv` function for finding the best lambda hyperparamater by cross-validation. Those are used only if `fitType` = `:path` or = `:all`.

**Optional keyword arguments for fitting the model(s) using GLMNet.jl**

`alpha`: the hyperparameter in $[0, 1]$ to trade-off an elestic-net model. *α=0* requests a pure *ridge* model and *α=1* a pure *lasso* model. This defaults to 1.0, which specifies a lasso model, unless the input [`ENLR`](@ref) `model` has another value in the `alpha` field, in which case this value is used. If argument `alpha` is passed here, it will overwrite the `alpha` field of the input `model`.

`weights`: a vector of weights for each matrix (or feature vectors) of the same size as `yTr`. It defaults to 1 for all matrices.

`intercept`: whether to fit an intercept term. The intercept is always unpenalized. Defaults to true.

If `fitType` = `:best` (default), a cross-validation procedure is run to find the best lambda hyperparameter for the given training data. This finds a single model that is written into the `.best` field of the [`ENLR`](@ref) structure that will be created.

If `fitType` = `:path`, the regularization path for several values of the lambda hyperparameter is found for the given training data. This creates several models, which are written into the `.path` field of the [`ENLR`](@ref) structure that will be created, none of which is optimal, in the cross-validation sense, for the given training data.

If `fitType` = `:all`, both the above fits are performed and all fields of the [`ENLR`](@ref) structure that will be created will be filled in.

`penalty_factor`: a vector of length *n(n+1)/2*, where *n* is the dimension of the original PD matrices on which the model is applied, of penalties for each predictor in the tangent vectors. This defaults to all ones, which weights each predictor equally. To specify that a predictor should be unpenalized, set the corresponding entry to zero.

`constraints`: an *[n(n+1)/2]* x *2* matrix specifying lower bounds (first column) and upper bounds (second column) on each predictor. By default, this is [-Inf Inf] for each predictor (each element of tangent vectors).

`offset`: see documentation of original GLMNet package [🎓](@ref).

`dfmax`: The maximum number of predictors in the largest model.

`pmax`: The maximum number of predictors in any model.

`nlambda`: The number of values of *λ* along the path to consider.

`lambda_min_ratio`: The smallest *λ* value to consider, as a ratio of the value of *λ* that gives the null model (*i.e.*, the model with only an intercept). If the number of observations exceeds the number of variables, this defaults to 0.0001, otherwise 0.01.

`lambda`: The *λ* values to consider for fitting. By default, this is determined from `nlambda` and `lambda_min_ratio`.

`maxit`: The maximum number of iterations of the cyclic coordinate descent algorithm. If convergence is not achieved, a warning is returned.

`algorithm`: the algorithm used to find the regularization path. Possible values are `:newtonraphson` (default) and `:modifiednewtonraphson`.

For further informations on those arguments, refer to the resources on the GLMNet package [🎓](@ref).

!!! warning "Possible change of dimension"
    The provided arguments `penalty_factor`, `constraints`, `dfmax`, `pmax` and  `lambda_min_ratio` will be ignored if a pre-conditioning `pipeline` is passed  as argument and if the pipeline	changes the dimension of the input matrices,  thus of the tangent vectors. In this case they will be set to their  default values using the new dimension. To force the use of the provided values  instead, set `checkArgs` to false (true by default). Note however that in this  case you must provide suitable values for all the abova arguments.


**Optional Keyword arguments for finding the best model by cv**

`λSelMeth` = `:sd1` (default), the best model is defined as the one allowing the highest `cvλ.meanloss` within one standard deviation of the minimum, otherwise it is defined as the one allowing the minimum `cvλ.meanloss`. Note that in selecting a model, the model with only the intercept term, if it exists, is ignored. See [`ENLRmodel`](@ref) for a description of the `.cvλ` field of the model structure.

Arguments `nfolds`, `folds` and `parallel` are passed to the `GLMNet.glmnetcv` function along with the `⏩` argument. Please refer to the resources on GLMNet for details [🎓](@ref).

`tol`: Is the convergence criterion for both the computation of a mean for projecting onto the tangent space (if the metric requires an iterative algorithm) and for the GLMNet fitting algorithm. Defaults to 1e-5. In order to speed up computations, you may try to set a lower `tol`; The convergence will be faster but more coarse, with a possible drop of classification accuracy, depending on the signal-to-noise ratio of the input features.

If `verbose` is true (default), information is printed in the REPL.

The `⏩` argument (true by default) is passed to the [`tsMap`](@ref) function for projecting the matrices in `𝐏Tr` onto the tangent space and to the `GLMNet.glmnetcv` function to run inner cross-validation to find the `best` model using multi-threading.

**See**: [notation & nomenclature](@ref), [the ℍVector type](@ref)

**See also**: [`predict`](@ref), [`crval`](@ref)

**Tutorial**: [Examples using the ENLR model](@ref)

**Examples**

```julia
using PosDefManifoldML, PosDefManifold

# Generate some data
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80, 0.1)

# Fit an ENLR lasso model and find the best model by cross-validation
m = fit(ENLR(), PTr, yTr)

# ... standardizing the tangent vectors
m = fit(ENLR(), PTr, yTr; pipeline=p, normalize=standardize!)

# ... balancing the weights for tangent space mapping
m = fit(ENLR(), PTr, yTr; w=tsWeights(yTr))

# ... using the log-Eucidean metric for tangent space projection
m = fit(ENLR(logEuclidean), PTr, yTr)

# Fit an ENLR ridge model and find the best model by cv:
m = fit(ENLR(Fisher), PTr, yTr; alpha=0)

# Fit an ENLR elastic-net model (α=0.9) and find the best model by cv:
m = fit(ENLR(Fisher), PTr, yTr; alpha=0.9)

# Fit an ENLR lasso model and its regularization path:
m = fit(ENLR(), PTr, yTr; fitType=:path)

# Fit an ENLR lasso model, its regularization path
# and the best model found by cv:
m = fit(ENLR(), PTr, yTr; fitType=:all)

# Fit using a pre-conditioning pipeline:
p = @→ Recenter(; eVar=0.999) Compress Shrink(Fisher; radius=0.02)
m = fit(ENLR(PosDefManifold.Euclidean), PTr, yTr; pipeline=p)

# Use a recentering pipeline and project the data
# onto the tangent space at the identity matrix.
# In this case the metric is irrilevant as the barycenter
# for determining the base point is not computed.
# Note that the previous call to 'fit' has modified `PTr`,
# so we generate new data.
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80, 0.1)
p = @→ Recenter(; eVar=0.999) Compress Shrink(Fisher; radius=0.02)
m = fit(ENLR(), PTr, yTr; pipeline=p, meanISR=I)
```
