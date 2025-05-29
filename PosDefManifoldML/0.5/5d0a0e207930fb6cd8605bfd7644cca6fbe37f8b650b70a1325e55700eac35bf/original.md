```julia
function crval(model    :: MLmodel,
               𝐏        :: ℍVector,
               y        :: IntVector;
        pipeline    :: Union{Pipeline, Nothing} = nothing,
        nFolds      :: Int     = min(10, length(y)÷3),
        shuffle     :: Bool    = false,
        scoring     :: Symbol  = :b,
        hypTest     :: Union{Symbol, Nothing} = :Bayle,
        verbose     :: Bool    = true,
        outModels   :: Bool    = false,
        ⏩           :: Bool    = true,
        fitArgs...)
```

Stratified cross-validation accuracy for a machine learning `model` given an ℍVector $𝐏$ holding *k* Hermitian matrices and an [IntVector](@ref) `y` holding the *k* labels for these matrices. Return a [`CVres`](@ref) structure.

For each fold, a machine learning model is fitted on training data and labels are predicted on testing data. Summary classification performance statistics are stored in the output structure.

**Optional keyword arguments**

If a `pipeline`, of type [`Pipeline`](@ref) is provided,  the pipeline is fitted on training data and applied for predicting the testing data.

`nFolds` by default is set to the minimum between 10 and the number of observation ÷ 3 (integer division).

If `scoring`=:b (default) the **balanced accuracy** is computed. Any other value will make the function returning the regular **accuracy**. Balanced accuracy is to be preferred for unbalanced classes. For balanced classes the balanced accuracy reduces to the regular accuracy, therefore there is no point in using regular accuracy if not to avoid a few unnecessary computations when the class are balanced.

!!! info "Error loss"
    Note that this function computes the error loss for each fold (see [`CVres`](@ref)). The average error loss is the complement of accuracy,  not of balanced accuracy. If the classes are balanced and you use `scoring`=:a (accuracy),  the average error loss within each fold is equal to 1 minus the average accuracy,  which is also computed by this function. However, this is not true if the classes are unbalanced and you use `scoring`=:b (default). In this case the returned error loss and accuracy may appear incoherent.


`hypTest` can be `nothing` or a symbol specifying the kind of statistical test to be carried out. At the moment, only `:Bayle` is a possible symbol and this test is performed by default. Bayle's procedure tests whether the average observed binary error loss is inferior to what is to be  expected by the hypothesis of random chance, which is set to $1-\frac{1}{z}$, where $z$ is the number of classes (see [`testCV`](@ref)).

For the meaning of the `shuffle` argument (false by default), see function [`cvSetup`](@ref), to which this argument is passed internally.

For the meaning of the `seed` argument (1234 by default), see function [`cvSetup`](@ref), to which this argument is passed internally.

If `verbose` is true (default), information is printed in the REPL.

If `outModels` is true, return a 2-tuple holding a [`CVres`](@ref) structure and a `nFolds`-vector of the model fitted for each fold, otherwise (default), return only a [`CVres`](@ref) structure.

If `⏩` the computations are multi-threaded across folds. It is true by default. Set it to false if there are problems in running this function and for debugging.

!!! note "Multi-threading"
    If you run the cross-validation with independent threads per fold setting `⏩=true`(default), the [`fit!`](@ref) and [`predict`](@ref) function that will be called within each fold will we run in single-threaded mode. Vice versa, if you pass `⏩=false`, these two functions will be run in multi-threaded mode. This is done to avoid overshooting the number of threads to be activated.


`fitArgs` are optional keyword arguments that are passed to the [`fit`](@ref) function called for each fold of the cross-validation. For each machine learning model, all optional keyword arguments of their fit method are elegible to be passed here, however, the arguments listed in the following table for each model should not be passed. Note that if they are passed, they will be disabled:

|  MDM/MDMF  |    ENLR    |    SVM     |
|:----------:|:----------:|:----------:|
| `verbose`  | `verbose`  | `verbose`  |
|    `⏩`     |    `⏩`     |    `⏩`     |
| `meanInit` | `meanInit` | `meanInit` |
| `meanISR`  | `fitType`  |            |
|            | `offsets`  |            |
|            |  `lambda`  |            |
|            |  `folds`   |            |

If you pass the `meanISR` argument, this must be nothing (default)  or I (the identity matrix). If you pass `meanISR=I` for a tangent space model, parallel transport of the points to the identity before projecting the points onto the tangent space will not be carried out. This can be used if a recentering conditioner is passed in the `pipeline` (see the [`fit`](@ref) method for the ENLR and SVM model).

Also, if you pass a `w` argument (weights for barycenter estimations), do not pass a vector of weights, just pass a symbol, *e.g.*, `w=:b` for balancing weights.

**See**: [notation & nomenclature](@ref), [the ℍVector type](@ref)

**See also**: [`fit`](@ref), [`predict`](@ref)

**Examples**

```julia
using PosDefManifoldML, PosDefManifold

# Generate some data
P, _dummyP, y, _dummyy = gen2ClassData(10, 60, 80, 30, 40, 0.2)

# Perform 10-fold cross-validation using the minimum distance to mean classifier
cv = crval(MDM(Fisher), P, y)

# Do the same applying a pre-conditioning pipeline
p = @→ Recenter(; eVar=0.999) Compress Shrink(Fisher; radius=0.02)
cv = crval(MDM(Fisher), P, y; pipeline = p)

# Apply a pre-conditioning pipeline and project the data 
# onto the tangent space at I without recentering the matrices.
# Note that this makes sense only for tangent space ML models.
p = @→ Recenter(; eVar=0.999) Compress Shrink(Fisher; radius=0.02)
cv = crval(ENLR(Fisher), P, y; pipeline = p, meanISR=I)

# Perform 10-fold cross-validation using the lasso logistic regression classifier
cv = crval(ENLR(Fisher), P, y)

# ...using the support-vector machine classifier
cv = crval(SVM(Fisher), P, y)

# ...with a Polynomial kernel of order 3 (default)
cv = crval(SVM(Fisher), P, y; kernel=kernel.Polynomial)

# Perform 8-fold cross-validation instead
# (and see that you can go pretty fast if your PC has 8 threads)
cv = crval(SVM(Fisher), P, y; nFolds=8)

# ...balance the weights for tangent space projection
cv = crval(ENLR(Fisher), P, y; nFolds=8, w=:b)

# perform another cross-validation shuffling the folds
cv = crval(ENLR(Fisher), P, y; shuffle=true, nFolds=8, w=:b)

```
