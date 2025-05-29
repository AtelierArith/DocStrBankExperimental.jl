```julia
function predict(model   :: ENLRmodel,
		𝐏Te         :: Union{ℍVector, Matrix{Float64}},
		what        :: Symbol = :labels,
		fitType     :: Symbol = :best,
		onWhich     :: Int    = Int(fitType==:best);
    pipeline    :: Union{Pipeline, Nothing} = nothing,
    meanISR     :: Union{ℍ, Nothing, UniformScaling} = nothing,
    verbose     :: Bool = true,
    ⏩          :: Bool = true)
```

Given an [`ENLR`](@ref) `model` trained (fitted) on 2 classes and a testing set of *k* positive definite matrices `𝐏Te` of type [ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1),

if `what` is `:labels` or `:l` (default), return the predicted **class labels** for each matrix in `𝐏Te`, as an [IntVector](@ref). Those labels are '1' for class 1 and '2' for class 2;

if `what` is `:probabilities` or `:p`, return the predicted **probabilities** for each matrix in `𝐏Te` to belong to each classe, as a *k*-vector of *z* vectors holding reals in *[0, 1]* (probabilities). The 'probabilities' are obtained passing to a [softmax function](https://en.wikipedia.org/wiki/Softmax_function) the output of the ENLR model and zero;

if `what` is `:f` or `:functions`, return the **output function** of the model, which is the raw output of the ENLR model.

If `fitType` = `:best` (default), the best model that has been found by cross-validation is used for prediction.

If `fitType` = `:path`,

  * if `onWhich` is a valid serial number for a model in the `model.path`,

then this model is used for prediction,

  * if `onWhich` is zero, all models in the `model.path` will be used for predictions, thus the output will be multiplied by the number of models in `model.path`.

Argument `onWhich` has no effect if `fitType` = `:best`.

!!! note "Nota Bene"
    By default, the [`fit`](@ref) function fits only the `best` model. If you want to use the `fitType` = `:path` option you need to invoke the fit function with optional keyword argument `fitType`=`:path` or `fitType`=`:all`. See the [`fit`](@ref) function for details.


Optional keyword argument `meanISR` can be used to specify the principal inverse square root (ISR) of a new mean to be used as base point for projecting the matrices in testing set `𝐏Te` onto the tangent space. By default `meanISR` is equal to nothing, implying that the base point will be the mean used to fit the model. This corresponds to the classical 'training-test' mode of operation.

Passing with argument `meanISR` a new mean ISR allows the *adaptation* first described in Barachant et *al.* (2013)[🎓](@ref). Typically `meanISR` is the ISR of the mean of the matrices in `𝐏Te` or of a subset of them. Notice that this actually performs *transfer learning* by parallel transporting both the training and test data to the identity matrix as defined in Zanini et *al.* (2018) and later taken up in Rodrigues et *al.* (2019)[🎓](@ref).   You can aslo pass `meanISR=I`, in which case the base point is taken as the identity matrix. This is possible if the set `𝐏Te` is centered to the identity, for instance, if a recentering pre-conditioner is included in a pipeline and the pipeline  is adapted as well (see the example below).

If `verbose` is true (default), information is printed in the REPL. This option is included to allow repeated calls to this function without crowding the REPL.

If ⏩ = true (default) and `𝐏Te` is an ℍVector type, the projection onto the tangent space is multi-threaded.

Note that if the field `pipeline` of the provided `model` is not `nothing`, implying that a pre-conditioning pipeline has been fitted during the fitting of the model, the pipeline is applied to the data before to carry out the prediction. If you wish to **adapt** the pipeline to the testing data,  just pass the same pipeline as argument `pipeline` in this function.

!!! warning "Adapting the Pipeline"
    Be careful when adapting a pipeline; if a [`Recenter`](@ref) conditioner is included in the pipeline and dimensionality reduction was sought (parameter `eVar` different  from `nothing`), then `eVar` must be set to an integer so that the dimension of the training ad testing data is the same after adaptation. See the example here below.


**See**: [notation & nomenclature](@ref), [the ℍVector type](@ref)

**See also**: [`fit`](@ref), [`crval`](@ref), [`predictErr`](@ref)

**Examples**

```julia
using PosDefManifoldML, PosDefManifold

# Generate some data
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80)

# Fit an ENLR lasso model and find the best model by cv
m = fit(ENLR(Fisher), PTr, yTr)

# Predict labels from the best model
yPred = predict(m, PTe, :l)

# Prediction error
predErr = predictErr(yTe, yPred)

# Predict probabilities from the best model
predict(m, PTe, :p)

# Output functions from the best model
predict(m, PTe, :f)

# Fit a regularization path for an ENLR lasso model
m = fit(ENLR(Fisher), PTr, yTr; fitType=:path)

# Predict labels using a specific model
yPred = predict(m, PTe, :l, :path, 10)

# Predict labels for all models
yPred = predict(m, PTe, :l, :path, 0)

# Prediction error for all models
predErr = [predictErr(yTe, yPred[:, i]) for i=1:size(yPred, 2)]

# Predict probabilities from a specific model
predict(m, PTe, :p, :path, 12)

# Predict probabilities from all models
predict(m, PTe, :p, :path, 0)

# Output functions from specific model
predict(m, PTe, :f, :path, 3)

# Output functions for all models
predict(m, PTe, :f, :path, 0)

## Adapting the base point
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80)
m = fit(ENLR(Fisher), PTr, yTr)
predict(m, PTe, :l; meanISR=invsqrt(mean(Fisher, PTe)))

# Also using and adapting a pre-conditioning pipeline
# For adaptation, we need to set `eVar` to an integer or to `nothing`.
# We will use the dimension determined on training data.
# Note that the adaptation does not work well if the class proportions
# of the training data is different from the class proportions of the test data.
p = @→ Recenter(; eVar=0.999) Compress Shrink(Fisher; radius=0.02)

# Fit the model using the pre-conditioning pipeline
m = fit(ENLR(), PTr, yTr; pipeline = p)

# Define the same pipeline with fixed dimensionality reduction parameter
p = @→ Recenter(; eVar=dim(m.pipeline)) Compress Shrink(Fisher; radius=0.02)

# Fit the pipeline to testing data (adapt) and use the identity matrix as base point:
predict(m, PTe, :l; pipeline=p, meanISR=I) 

# Suppose we want to adapt recentering, but not shrinking, which also has a 
# learnable parameter. We would then use this pipeline instead:
p = deepcopy(m.pipeline)
p[1].eVar = dim(m.pipeline)
```
