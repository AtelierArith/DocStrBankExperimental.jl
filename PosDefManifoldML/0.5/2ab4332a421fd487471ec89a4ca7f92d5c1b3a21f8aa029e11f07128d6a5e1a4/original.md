```julia
mutable struct MDM <: MDMmodel
    metric  :: Metric = Fisher;
    pipeline :: Pipeline
    featDim :: Int
    means   :: ℍVector
    imeans  :: ℍVector
end
```

MDM machine learning models are incapsulated in this mutable structure. MDM models have four fields: `.metric`, `.pipeline`, `.featDim` and `.means`.

The field `metric`, of type [Metric](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#Metric::Enumerated-type-1), is to be specified by the user. It is the metric that will be adopted to compute the class means and the distances to the mean.

All other fields do not correspond to arguments passed upon creation of the model by the default creator. Instead, they are filled later when a model is created by the [`fit`](@ref) function:

The field `pipeline`, of type [`Pipeline`](@ref), holds an optional sequence of data pre-conditioners to be applied to the data.  The pipeline is learnt when a ML model is fitted - see [`fit`](@ref) -  and stored in the model. If the pipeline is fitted, it is  automatically applied to the data at each call of the [`predict`](@ref) function.

The field `featDim` is the dimension of the manifold in which the model acts. This is given by *n(n+1)/2*, where *n* is the dimension of the PD matrices. This field is not to be specified by the user, instead, it is computed when the MDM model is fit using the [`fit`](@ref) function and is accessible only thereafter.

The field `means` is an [ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1) holding the class means, *i.e.*, one mean for each class. This field is not to be specified by the user, instead, the means are computed when the MDM model is fitted using the [`fit`](@ref) function and are accessible only thereafter.

The field `imeans` is an ℍVector holding the inverse of the matrices in `means`. This also is not to be specified by the user, is computed when the model is fitted and is accessible only thereafter. It is used to optimize the computation of distances if the model is fitted useing the Fisher metric (default).

**Examples**:

```julia
using PosDefManifoldML, PosDefManifold

# Create an empty model
m = MDM(Fisher)

# Since the Fisher metric is the default metric,
# this is equivalent to
m = MDM()
```

Note that in general you need to invoke these constructors only when an empty MDM model is needed as an argument to a function, otherwise you can more simply create and fit an MDM model using the [`fit`](@ref) function.
