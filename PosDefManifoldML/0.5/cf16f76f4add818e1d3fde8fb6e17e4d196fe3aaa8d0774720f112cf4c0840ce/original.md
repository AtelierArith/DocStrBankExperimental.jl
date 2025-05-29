```julia
function fit(model :: MDMmodel,
              𝐏Tr   :: ℍVector,
              yTr   :: IntVector;
        pipeline :: Union{Pipeline, Nothing} = nothing,
        w        :: Vector = [],
        ✓w       :: Bool  = true,
        meanInit :: Union{ℍVector, Nothing} = nothing,
        tol      :: Real  = 1e-5,
        verbose  :: Bool  = true,
        ⏩       :: Bool  = true)
```

Fit an [`MDM`](@ref) machine learning model, with training data `𝐏Tr`, of type [ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1), and corresponding labels `yTr`, of type [IntVector](@ref). Return the fitted model.

!!! warning "Class Labels"
    Labels must be provided using the natural numbers, *i.e.*, `1` for the first class, `2` for the second class, etc.


Fitting an MDM model involves only computing a mean (barycenter) of all the matrices in each class. Those class means are computed according to the metric specified by the [`MDM`](@ref) constructor.

**Optional keyword arguments:** 

If a `pipeline`, of type [`Pipeline`](@ref) is provided,  all necessary parameters of the sequence of conditioners are fitted and all matrices  are transformed according to the specified pipeline before fitting the ML model. The parameters are stored in the output ML model. Note that the fitted pipeline is automatically applied by any successive call  to function [`predict`](@ref) to which the output ML model is passed as argument.

`w` is a vector of non-negative weights associated with the matrices in `𝐏Tr`. This weights are used to compute the mean for each class. See method (3) of the [mean](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#Statistics.mean) function for the meaning of the arguments `w`, `✓w` and `⏩`, to which they are passed. Keep in mind that here the weights should sum up to 1 separatedly for each class, which is what is ensured by this function if `✓w` is true.

`tol` is the tolerance required for those algorithms that compute the mean iteratively (they are those adopting the Fisher, logdet0 or Wasserstein metric). It defaults to 1e-5. For details on this argument see the functions that are called for computing the means (from package *PosDefManifold.jl*):

  * Fisher metric: [gmean](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.geometricMean)
  * logdet0 metric: [ld0mean](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.logdet0Mean)
  * Wasserstein metric: [Wasmean](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.wasMean).

For those algorithm an initialization can be provided with optional keyword argument `meanInit`. If provided, this must be a vector of `Hermitian` matrices of the [ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%F0%9D%95%84Vector-type-1) type and must contain as many initializations as classes, in the natural order corresponding to the class labels (see above).

If `verbose` is true (default), information is printed in the REPL.

**See**: [notation & nomenclature](@ref), [the ℍVector type](@ref)

**See also**: [`predict`](@ref), [`crval`](@ref)

**Examples**

```julia
using PosDefManifoldML, PosDefManifold

# Generate some data
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80, 0.25)

# Create and fit a model:
m = fit(MDM(Fisher), PTr, yTr)

# Create and fit a model using a pre-conditioning pipeline:
p = @→ Recenter(; eVar=0.999) Compress Shrink(Fisher; radius=0.02)
m = fit(MDM(Fisher), PTr, yTr; pipeline=p)
```
