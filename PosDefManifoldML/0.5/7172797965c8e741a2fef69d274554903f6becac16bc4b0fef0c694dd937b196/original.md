```julia
function predict(model  :: MDMmodel,
                 𝐏Te    :: ℍVector,
                 what   :: Symbol = :labels;
        pipeline    :: Union{Pipeline, Nothing} = nothing,
        verbose     :: Bool = true,
        ⏩          :: Bool = true)
```

Given an [`MDM`](@ref) `model` trained (fitted) on *z* classes and a testing set of *k* positive definite matrices `𝐏Te` of type [ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1):

if `what` is `:labels` or `:l` (default), return the predicted **class labels** for each matrix in `𝐏Te`, as an [IntVector](@ref). For MDM models, the predicted class 'label' of an unlabeled matrix is the serial number of the class whose mean is the closest to the matrix (minimum distance to mean). The labels are '1' for class 1, '2' for class 2, etc;

if `what` is `:probabilities` or `:p`, return the predicted **probabilities** for each matrix in `𝐏Te` to belong to all classes, as a *k*-vector of *z* vectors holding reals in $[0, 1]$. The 'probabilities' are obtained passing to a [softmax function](https://en.wikipedia.org/wiki/Softmax_function) the squared distances of each unlabeled matrix to all class means with inverted sign;

if `what` is `:f` or `:functions`, return the **output function** of the model as a *k*-vector of *z* vectors holding reals. The function of each element in `𝐏Te` is the ratio of the  squared distance from each class to the (scalar) geometric mean of the  squared distances from all classes.

If `verbose` is true (default), information is printed in the REPL.

It f `⏩` is true (default), the computation of distances is multi-threaded.

Note that if the field `pipeline` of the provided `model` is not `nothing`, implying that a pre-conditioning pipeline has been fitted, the pipeline is applied to the data before to carry out the prediction. If you wish to **adapt** the pipeline to the testing data,  just fit the pipeline to the testing data overwriting the model pipeline. This is useful in a cross-session and cross-subject setting.

!!! warning "Adapting the Pipeline"
    Be careful when adapting a pipeline; if a [`Recenter`](@ref) conditioner is included in the pipeline and dimensionality reduction was sought (parameter `eVar` different  from `nothing`), then `eVar` must be set to an integer so that the dimension of the training ad testing data is the same after adaptation. See the example here below.


**See**: [notation & nomenclature](@ref), [the ℍVector type](@ref)

**See also**: [`fit`](@ref), [`crval`](@ref), [`predictErr`](@ref)

**Examples**

```julia
using PosDefManifoldML, PosDefManifold

# Generate some data
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80)

# Craete and fit an MDM model
m = fit(MDM(Fisher), PTr, yTr)

# Predict labels
yPred = predict(m, PTe, :l)

# Prediction error
predErr = predictErr(yTe, yPred)

# Predict probabilities
predict(m, PTe, :p)

# Output functions
predict(m, PTe, :f)

# Using and adapting a pipeline

# get some random data and labels as an example
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80)

# For adaptation, we need to set `eVar` to an integer or to `nothing`.
# We will use the dimension determined on training data.
# Note that the adaptation does not work well if the class proportions
# of the training data is different from the class proportions of the test data.
p = @→ Recenter(; eVar=0.999) Compress Shrink(Fisher; radius=0.02)

# Fit the model using the pre-conditioning pipeline
m = fit(MDM(), PTr, yTr; pipeline = p)

# Define the same pipeline with fixed dimensionality reduction parameter
p = @→ Recenter(; eVar=dim(m.pipeline)) Compress Shrink(Fisher; radius=0.02)

# Fit the pipeline to testing data (adapt):
predict(m, PTe, :l; pipeline=p) 

# Suppose we want to adapt recentering, but not shrinking, which also has a 
# learnable parameter. We would then use this pipeline instead:
p = deepcopy(m.pipeline)
p[1].eVar = dim(m.pipeline)
```
