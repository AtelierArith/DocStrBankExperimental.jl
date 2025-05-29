```
ObsView(data, [obsdim])
```

# Description

Create a view of the given `data` in the form of a vector of individual observations. Any data access is delayed until `getindex` is called, and even `getindex` returns the result of [`datasubset`](@ref) which in general avoids data movement until [`getobs`](@ref) is called.

If used as an iterator, the view will iterate over the dataset once, effectively denoting an epoch. Each iteration will return a lazy subset to the current observation.

# Arguments

  * **`data`** : The object describing the dataset. Can be of any   type as long as it implements [`getobs`](@ref) and   [`nobs`](@ref) (see Details for more information).
  * **`obsdim`** : Optional. If it makes sense for the type of   `data`, `obsdim` can be used to specify which dimension of   `data` denotes the observations. It can be specified in a   type-stable manner as a positional argument (see   `?LearnBase.ObsDim`), or more conveniently as a smart keyword   argument.

# Methods

Aside from the `AbstractArray` interface following additional methods are provided:

  * **`getobs(data::ObsView, indices::AbstractVector)`** :   Returns a `Vector` of indivdual observations specified by   `indices`.
  * **`nobs(data::ObsView)`** :   Returns the number of observations in `data` that the   iterator will go over.

# Details

For `ObsView` to work on some data structure, the type of the given variable `data` must implement the data container interface. See `?DataSubset` for more info.

# Author(s)

  * Christof Stocker (Github: https://github.com/Evizero)
  * Tom Breloff (Github: https://github.com/tbreloff)

# Examples

```julia
X, Y = MLDataUtils.load_iris()

A = obsview(X)
@assert typeof(A) <: ObsView <: AbstractVector
@assert eltype(A) <: SubArray{Float64,1}
@assert length(A) == 150 # Iris has 150 observations
@assert size(A[1]) == (4,) # Iris has 4 features

for x in obsview(X)
    @assert typeof(x) <: SubArray{Float64,1}
end

# iterate over each individual labeled observation
for (x,y) in obsview((X,Y))
    @assert typeof(x) <: SubArray{Float64,1}
    @assert typeof(y) <: String
end

# same but in random order
for (x,y) in obsview(shuffleobs((X,Y)))
    @assert typeof(x) <: SubArray{Float64,1}
    @assert typeof(y) <: String
end
```

# see also

[`eachobs`](@ref), [`BatchView`](@ref), [`shuffleobs`](@ref), [`getobs`](@ref), [`nobs`](@ref), [`DataSubset`](@ref)
