```julia
mutable struct SVM <: SVMmodel
	metric		:: Metric
	svmType		:: Type
	kernel		:: Kernel.KERNEL
	pipeline 	:: Pipeline
	normalize	:: Union{Function, Tuple, Nothing}
	meanISR		:: Union{HermitianVector, Nothing, UniformScaling}
	vecRange	:: UnitRange
	featDim		:: Int
	svmModel #store the training model from the SVM library
```

SVM machine learning models are incapsulated in this mutable structure. Fields:

`.metric`, of type [Metric](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#Metric::Enumerated-type-1), is the metric that will be adopted to compute the mean used as base-point for tangent space projection. By default the Fisher metric is adopted. See [mdm.jl](@ref) for the available metrics. If the data used to train the model are not positive definite matrices, but Euclidean feature vectors, the `.metric` field has no use.  In order to use metrics you need to install the *PosDefManifold* package.

`svmType`, a generic Type of SVM models used in LIBSVM. Available types are:

  * `SVC`: *C-Support Vector Classification*. The fit time complexity is more  than quadratic with the number of observations. The multiclass support is handled  according to a one-vs-one scheme,
  * `NuSVC`: *Nu-Support Vector Classification*. Similar to SVC but uses a  parameter to control the number of support vectors,
  * `OneClassSVM`: Unsupervised outlier detection. Estimate the support of a high-dimensional distribution,
  * `EpsilonSVR`: *Epsilon-Support Vector Regression*,
  * `NuSVR`: *Nu-Support Vector Regression*.

The default is `SVC`, unless labels are not provided while fitting the model, in which case it defaults to `OneClassSVM`.

`kernel`, a kernel type. Available kernels are declared as constants in the main module. They are:

  * `Linear` 		(default)
  * `RadialBasis`
  * `Polynomial`
  * `Sigmoid`
  * `Precomputed` (not supported).

All other fields do not correspond to arguments passed upon creation of the model by the default creator. Instead, they are filled later when a model is created by the [`fit`](@ref) function:

For the content of fields `vecRange` and `normalize`, please see the documentation of the [`fit`](@ref) function for the ENLR model.

For the content of the `.meanISR`, `.featDim` and `pipeline` fields please see the documentation of the [`ENLR`](@ref) structure.

`svmModel` holds the model structure created by LIBSVM when the model is fitted (declared [here](https://github.com/mpastell/LIBSVM.jl/blob/master/src/LibSVMtypes.jl)).

**Examples**:

```julia
# Note: creating models with the default creator is possible,
# but not useful in general.

using PosDefManifoldML, PosDefManifold

# Create an empty SVM model
m = SVM(Fisher)

# Since the Fisher metric is the default metric,
# this is equivalent to
m = SVM()

# Create an empty SVM model using the logEuclidean metric
m = SVM(logEuclidean)

# Generate some data
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80, 0.1);

# Empty models can be passed as first argument of the `fit` function
# to fit a model. For instance, this will fit an SVM model of the same
# kind of `m` and put the fitted model in `m1`:
m1 = fit(m, PTr, yTr)

# In general you don't need this machinery for fitting a model,
# since you can specify a model by creating one on the fly:
m2 = fit(SVM(logEuclidean), PTr, yTr; kernel=Linear)

# which is equivalent to
m2 = fit(m, PTr, yTr; kernel=Linear)

# note that, albeit model `m` has been created as an SVM model
# with the default kernel (RadialBasis),
# you have passed `m` and overwritten the `kernel` type.
# You can also overwrite the `svmType`.
# The metric, instead, cannot be overwritten.
```
