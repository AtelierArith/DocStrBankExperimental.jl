```
BatchView(data, [size|maxsize], [count], [obsdim])
```

# Description

Create a view of the given `data` that represents it as a vector of batches. Each batch will contain an equal amount of observations in them. The number of batches and the batch-size can be specified using (keyword) parameters `count` and `size`. In the case that the size of the dataset is not dividable by the specified (or inferred) `size`, the remaining observations will be ignored with a warning.

Note that any data access is delayed until `getindex` is called, and even `getindex` returns the result of [`datasubset`](@ref) which in general avoids data movement until [`getobs`](@ref) is called.

If used as an iterator, the object will iterate over the dataset once, effectively denoting an epoch. Each iteration will return a mini-batch of constant [`nobs`](@ref), which effectively allows to iterator over [`data`](@ref) one batch at a time.

# Arguments

  * **`data`** : The object describing the dataset. Can be of any   type as long as it implements [`getobs`](@ref) and   [`nobs`](@ref) (see Details for more information).
  * **`size`** : The batch-size of each batch. I.e. the number of   observations that each batch must contain.
  * **`maxsize`** : The maximum batch-size of each batch. I.e. the   number of observations that each batch should contain. If the   number of total observation is not divideable by the size it   will be reduced until it is.
  * **`count`** : The number of batches that the view will contain.
  * **`obsdim`** : Optional. If it makes sense for the type of   `data`, `obsdim` can be used to specify which dimension of   `data` denotes the observations. It can be specified in a   type-stable manner as a positional argument (see   `?LearnBase.ObsDim`), or more conveniently as a smart keyword   argument.

# Methods

Aside from the `AbstractArray` interface following additional methods are provided.

  * **`getobs(data::BatchView, batchindices)`** :   Returns a `Vector` of the batches specified by `batchindices`.
  * **`nobs(data::BatchView)`** :   Returns the total number of observations in `data`. Note that   unless the batch-size is 1, this number will differ from   `length`.

# Details

For `BatchView` to work on some data structure, the type of the given variable `data` must implement the data container interface. See `?DataSubset` for more info.

# Author(s)

  * Christof Stocker (Github: https://github.com/Evizero)
  * Tom Breloff (Github: https://github.com/tbreloff)

# Examples

```julia
using MLDataUtils
X, Y = MLDataUtils.load_iris()

A = batchview(X, size = 30)
@assert typeof(A) <: BatchView <: AbstractVector
@assert eltype(A) <: SubArray{Float64,2}
@assert length(A) == 5 # Iris has 150 observations
@assert size(A[1]) == (4,30) # Iris has 4 features

# 5 batches of size 30 observations
for x in batchview(X, size = 30)
    @assert typeof(x) <: SubArray{Float64,2}
    @assert nobs(x) === 30
end

# 7 batches of size 20 observations
# Note that the iris dataset has 150 observations,
# which means that with a batchsize of 20, the last
# 10 observations will be ignored
for (x,y) in batchview((X,Y), size = 20)
    @assert typeof(x) <: SubArray{Float64,2}
    @assert typeof(y) <: SubArray{String,1}
    @assert nobs(x) === nobs(y) === 20
end

# 10 batches of size 15 observations
for (x,y) in batchview((X,Y), maxsize = 20)
    @assert typeof(x) <: SubArray{Float64,2}
    @assert typeof(y) <: SubArray{String,1}
    @assert nobs(x) === nobs(y) === 15
end

# randomly assign observations to one and only one batch.
for (x,y) in batchview(shuffleobs((X,Y)))
    @assert typeof(x) <: SubArray{Float64,2}
    @assert typeof(y) <: SubArray{String,1}
end

# iterate over the first 2 batches of 15 observation each
for (x,y) in batchview((X,Y), size=15, count=2)
    @assert typeof(x) <: SubArray{Float64,2}
    @assert typeof(y) <: SubArray{String,1}
    @assert size(x) == (4, 15)
    @assert size(y) == (15,)
end
```

# see also

[`eachbatch`](@ref), [`ObsView`](@ref), [`shuffleobs`](@ref), [`getobs`](@ref), [`nobs`](@ref), [`DataSubset`](@ref)
