```julia
function fit(model     :: SVMmodel,
               𝐏Tr     :: Union{HermitianVector, Matrix{Float64}},
               yTr     :: IntVector=[];

	# pipeline (data transformations)
	pipeline    :: Union{Pipeline, Nothing} = nothing,

	# parameters for projection onto the tangent space
	w		:: Union{Symbol, Tuple, Vector} = Float64[],
	meanISR 	:: Union{Hermitian, Nothing, UniformScaling} = nothing,
	meanInit 	:: Union{Hermitian, Nothing} = nothing,
	vecRange	:: UnitRange = 𝐏Tr isa HermitianVector ? (1:size(𝐏Tr[1], 2)) : (1:size(𝐏Tr, 2)),
	normalize	:: Union{Function, Tuple, Nothing} = normalize!,

	# SVM parameters
	svmType 	:: Type = SVC,
	kernel 		:: Kernel.KERNEL = Linear,
	epsilon 	:: Float64 = 0.1,
	cost		:: Float64 = 1.0,
	gamma 		:: Float64	= 1/_getDim(𝐏Tr, vecRange),
	degree 		:: Int64	= 3,
	coef0 		:: Float64	= 0.,
	nu 			:: Float64 = 0.5,
	shrinking 	:: Bool = true,
	probability	:: Bool = false,
	weights 	:: Union{Dict{Int, Float64}, Nothing} = nothing,
	cachesize 	:: Float64	= 200.0,
	checkArgs	:: Bool = true,

	# Generic and common parameters
	tol		:: Real = 1e-5,
	verbose		:: Bool = true,
	⏩		:: Bool = true)
```

Create and fit a **1-class** or **2-class** support vector machine ([`SVM`](@ref)) machine learning model, with training data `𝐏Tr`, of type [ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1), and corresponding labels `yTr`, of type [IntVector](@ref). The label vector can be omitted if the `svmType` is `OneClassSVM` (see [`SVM`](@ref)). Return the fitted model as an instance of the [`SVM`](@ref) structure.

!!! warning "Class Labels"
    Labels must be provided using the natural numbers, *i.e.*, `1` for the first class, `2` for the second class, etc.


As for all ML models acting in the tangent space, fitting an SVM model involves computing a mean (barycenter) of all the matrices in `𝐏Tr`, projecting all matrices onto the tangent space after parallel transporting them at the identity matrix and vectorizing them using the [vecP](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.vecP) operation. Once this is done, the support-vector machine is fitted.

**Optional keyword arguments**

For the following keyword arguments see the documentation of the [`fit`](@ref)  funtion for the ENLR (Elastic Net Logistic Regression) machine learning model:

  * `pipeline` (pre-conditioning),
  * `w`, `meanISR`, `meanInit`, `vecRange` (tangent space projection),

!!! tip "Euclidean SVM models"
    ML models acting on the tangent space allows to fit a model passing as training data `𝐏Tr` directly a matrix of feature vectors, where each feature vector is a row of the matrix. In this case none of the above keyword arguments are used.


  * `normalize` (tangent or feature vectors normalization).

**Optional keyword arguments for fitting the model(s) using LIBSVM.jl**

`svmType` and `kernel` allow to chose among several available SVM models. See the documentation of the [`SVM`](@ref) structure.

`epsilon`, with default 0.1, is the epsilon in loss function of the `epsilonSVR` SVM model.

`cost`, with default 1.0, is the cost parameter *C* of `SVC`, `epsilonSVR`, and `nuSVR` SVM models.

`gamma`, defaulting to 1 divided by the length of the tangent (or feature) vectors, is the *γ* parameter for `RadialBasis`, `Polynomial` and `Sigmoid` kernels. The provided argument `gamma` will be ignored if a pre-conditioning `pipeline`  is passed as argument and if the pipeline changes the dimension of the input matrices,  thus of the tangent vectors. In this case it will be set to its default value using  the new dimension. To force the use of the provided `gamma` value instead,  set	`checkArgs` to false (true by default).

`degree`, with default 3, is the degree for `Polynomial` kernels

`coef0`, zero by default, is a parameter for the `Sigmoid` and `Polynomial` kernel.

`nu`, with default 0.5, is the parameter *ν* of `nuSVC`, `OneClassSVM`, and `nuSVR` SVM models. It should be in the interval (0, 1].

`shrinking`, true by default, sets whether to use the shrinking heuristics.

`probability`, false by default sets whether to train a `SVC` or `SVR` model allowing probability estimates.

if a `Dict{Int, Float64}` is passed as `weights` argument, it will be used to give weights to the classes. By default it is equal to `nothing`, implying equal weights to all classes.

`cachesize` for the kernel, 200.0 by defaut (in MB), can be increased for very large problems.

`tol` is the convergence criterion for both the computation of a mean for projecting onto the tangent space (if the metric requires an iterative algorithm) and for the LIBSVM fitting algorithm. Defaults to 1e-5.

If `verbose` is true (default), information is printed in the REPL. This option is included to allow repeated calls to this function without crowding the REPL. 

The `⏩` argument (true by default) is passed to the [`tsMap`](@ref) function for projecting the matrices in `𝐏Tr` onto the tangent space and to the LIBSVM function that perform the fit in order to run them in multi-threaded mode.

For further information on tho LIBSVM arguments, refer to the resources on the LIBSVM package [🎓](@ref).

**See**: [notation & nomenclature](@ref), [the ℍVector type](@ref)

**See also**: [`predict`](@ref), [`crval`](@ref)

**Tutorial**: [Examples using SVM models](@ref)

**Examples**

```julia
using PosDefManifoldML, PosDefManifold

# Generate some data
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80, 0.1);

# Fit a SVC SVM model and find the best model by cross-validation:
m = fit(SVM(), PTr, yTr)

# ... balancing the weights for tangent space mapping
m = fit(SVM(), PTr, yTr; w=:b)

# ... using the log-Eucidean metric for tangent space projection
m = fit(SVM(logEuclidean), PTr, yTr)

# ... using the linear kernel
m = fit(SVM(logEuclidean), PTr, yTr, kernel=Linear)

# or

m = fit(SVM(logEuclidean; kernel=Linear), PTr, yTr)

# ... using the Nu-Support Vector Classification
m = fit(SVM(logEuclidean), PTr, yTr, kernel=Linear, svmtype=NuSVC)

# or

m = fit(SVM(logEuclidean; kernel=Linear, svmtype=NuSVC), PTr, yTr)

# N.B. all other keyword arguments must be passed to the fit function
# and not to the SVM constructor.

# Fit a SVC SVM model using a pre-conditioning pipeline:
p = @→ Recenter(; eVar=0.999) Compress Shrink(Fisher; radius=0.02)
m = fit(SVM(PosDefManifold.Euclidean), PTr, yTr; pipeline=p)

# Use a recentering pipeline and project the data
# onto the tangent space at the identity matrix.
# In this case the metric is irrilevant as the barycenter
# for determining the base point is not computed.
# Note that the previous call to 'fit' has modified `PTr`,
# so we generate new data.
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80, 0.1)
p = @→ Recenter(; eVar=0.999) Compress Shrink(Fisher; radius=0.02)
m = fit(SVM(), PTr, yTr; pipeline=p, meanISR=I)
```
