```
DataSubset(data, [indices], [obsdim])
```

# Description

Used to represent a subset of some `data` of arbitrary type by storing which observation-indices the subset spans. Furthermore, subsequent subsettings are accumulated without needing to access actual data.

The main purpose for the existence of `DataSubset` is to delay data access and movement until an actual batch of data (or single observation) is needed for some computation. This is particularily useful when the data is not located in memory, but on the hard drive or some remote location. In such a scenario one wants to load the required data only when needed.

This type is usually not constructed manually, but instead instantiated by calling [`datasubset`](@ref), [`shuffleobs`](@ref), or [`splitobs`](@ref)

In case `data` is some `Tuple`, the constructor will be mapped over its elements. That means that the constructor returns a `Tuple` of `DataSubset` instead of a `DataSubset` of `Tuple`.

# Arguments

  * **`data`** : The object describing the dataset. Can be of any   type as long as it implements [`getobs`](@ref) and   [`nobs`](@ref) (see Details for more information).
  * **`indices`** : Optional. The index or indices of the   observation(s) in `data` that the subset should represent.   Can be of type `Int` or some subtype of `AbstractVector`.
  * **`obsdim`** : Optional. If it makes sense for the type of `data`,   `obsdim` can be used to specify which dimension of `data`   denotes the observations. It can be specified in a type-stable   manner as a positional argument (see `?LearnBase.ObsDim`), or   more conveniently as a smart keyword argument.

# Methods

  * **`getindex`** : Returns the observation(s) of the given   index/indices as a new `DataSubset`. No data is copied aside   from the required indices.
  * **`nobs`** : Returns the total number observations in the subset   (**not** the whole data set underneath).
  * **`getobs`** : Returns the underlying data that the   `DataSubset` represents at the given relative indices. Note   that these indices are in "subset space", and in general will   not directly correspond to the same indices in the underlying   data set.

# Details

For `DataSubset` to work on some data structure, the desired type `MyType` must implement the following interface:

  * `LearnBase.getobs(data::MyType, idx, [obsdim::ObsDimension])` :   Should return the observation(s) indexed by `idx`.   In what form is up to the user.   Note that `idx` can be of type `Int` or `AbstractVector`.
  * `StatsBase.nobs(data::MyType, [obsdim::ObsDimension])` :   Should return the total number of observations in `data`

The following methods can also be provided and are optional:

  * `LearnBase.getobs(data::MyType)` :   By default this function is the identity function.   If that is not the behaviour that you want for your type,   you need to provide this method as well.
  * `LearnBase.datasubset(data::MyType, idx, obsdim::ObsDimension)` :   If your custom type has its own kind of subset type, you can   return it here. An example for such a case are `SubArray` for   representing a subset of some `AbstractArray`.   Note: If your type has no use for `obsdim` then dispatch on   `::ObsDim.Undefined` in the signature.
  * `LearnBase.getobs!(buffer, data::MyType, [idx], [obsdim::ObsDimension])` :   Inplace version of `getobs(data, idx, obsdim)`. If this method   is provided for `MyType`, then `eachobs` and `eachbatch`   (among others) can preallocate a buffer that is then reused   every iteration. Note: `buffer` should be equivalent to the   return value of `getobs(::MyType, ...)`, since this is how   `buffer` is preallocated by default.
  * `LearnBase.gettargets(data::MyType, idx, [obsdim::ObsDimension])` :   If `MyType` has a special way to query targets without   needing to invoke `getobs`, then you can provide your own   logic here. This can be useful when the targets of your are   always loaded as metadata, while the data itself remains on   the hard disk until actually needed.

# Author(s)

  * Christof Stocker (Github: https://github.com/Evizero)
  * Tom Breloff (Github: https://github.com/tbreloff)

# Examples

```julia
X, y = MLDataUtils.load_iris()

# The iris set has 150 observations and 4 features
@assert size(X) == (4,150)

# Represents the 80 observations as a DataSubset
subset = DataSubset(X, 21:100)
@assert nobs(subset) == 80
@assert typeof(subset) <: DataSubset
# getobs indexes into the subset
@assert getobs(subset, 1:10) == X[:, 21:30]

# You can also work with data that uses some other dimension
# to denote the observations.
@assert size(X') == (150,4)
subset = DataSubset(X', 21:100, obsdim = :first) # or "obsdim = 1"
@assert nobs(subset) == 80

# To specify the obsdim in a type-stable way, use positional arguments
# provided by the submodule `ObsDim`.
@inferred DataSubset(X', 21:100, ObsDim.First())

# Subsets also works for tuple of data. (useful for labeled data)
subset = DataSubset((X,y), 1:100)
@assert nobs(subset) == 100
@assert typeof(subset) <: Tuple # Tuple of DataSubset

# The lowercase version tries to avoid boxing into DataSubset
# for types that provide a custom "subset", such as arrays.
# Here it instead creates a native SubArray.
subset = datasubset(X, 1:100)
@assert nobs(subset) == 100
@assert typeof(subset) <: SubArray

# Also works for tuples of arbitrary length
subset = datasubset((X,y), 1:100)
@assert nobs(subset) == 100
@assert typeof(subset) <: Tuple # tuple of SubArray

# Split dataset into training and test split
train, test = splitobs(shuffleobs((X,y)), at = 0.7)
@assert typeof(train) <: Tuple # of SubArray
@assert typeof(test)  <: Tuple # of SubArray
@assert nobs(train) == 105
@assert nobs(test) == 45
```

# see also

[`datasubset`](@ref),  [`getobs`](@ref), [`nobs`](@ref), [`splitobs`](@ref), [`shuffleobs`](@ref), [`KFolds`](@ref), [`BatchView`](@ref), [`ObsView`](@ref),
