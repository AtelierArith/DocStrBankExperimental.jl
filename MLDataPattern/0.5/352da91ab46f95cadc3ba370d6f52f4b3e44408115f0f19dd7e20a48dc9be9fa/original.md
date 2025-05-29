```
RandomBatches(data, [size], [count], [obsdim])
```

# Description

Create an iterator that generates `count` randomly sampled batches from `data` with a batch-size of `size` . In the case `count` is not provided, it will generate random batches indefinitely.

# Arguments

  * **`data`** : The object describing the dataset. Can be of any   type as long as it implements [`getobs`](@ref) and   [`nobs`](@ref) (see Details for more information).
  * **`size`** : Optional. The batch-size of each batch.   I.e. the number of randomly sampled observations in each batch
  * **`count`** : Optional. The number of randomly sampled batches   that the iterator will generate before stopping. If omitted,   the iterator will generate randomly sampled batches forever.
  * **`obsdim`** : Optional. If it makes sense for the type of   `data`, `obsdim` can be used to specify which dimension of   `data` denotes the observations. It can be specified in a   type-stable manner as a positional argument (see   `?LearnBase.ObsDim`), or more conveniently as a smart keyword   argument.

# Details

For `RandomBatches` to work on some data structure, the type of given variable `data` must implement the data container interface. See `?DataSubset` for more info.

# Author(s)

  * Christof Stocker (Github: https://github.com/Evizero)
  * Tom Breloff (Github: https://github.com/tbreloff)

# Examples

```julia
X, Y = MLDataUtils.load_iris()

# go over 500 randomly sampled batches of batchsize 10
i = 0
for x in RandomBatches(X, 10, 500) # also: RandomObs(X, size = 10, count = 500)
    @assert typeof(x) <: SubArray{Float64,2}
    @assert size(x) == (4,10)
    i += 1
end
@assert i == 500

# if no count it provided the iterator will generate samples forever
for x in RandomBatches(X, 10)
    # this loop will never stop unless break is used
    if true; break; end
end

# also works for multiple data arguments (e.g. labeled data)
for (x,y) in RandomBatches((X,Y), 10, 500)
    @assert typeof(x) <: SubArray{Float64,2}
    @assert typeof(y) <: SubArray{String,1}
end
```

# see also

[`RandomObs`](@ref), [`BatchView`](@ref), [`ObsView`](@ref), [`shuffleobs`](@ref), [`DataSubset`](@ref), [`BufferGetObs`](@ref)
