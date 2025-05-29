```
RandomObs(data, [count], [obsdim])
```

# Description

Create an iterator that generates `count` randomly sampled observations from `data`. In the case `count` is not provided, it will generate random samples indefinitely.

# Arguments

  * **`data`** : The object describing the dataset. Can be of any   type as long as it implements [`getobs`](@ref) and   [`nobs`](@ref) (see Details for more information).
  * **`count`** : Optional. The number of randomly sampled   observations that the iterator will generate before stopping.   If omitted, the iterator will generate randomly sampled   observations forever.
  * **`obsdim`** : Optional. If it makes sense for the type of   `data`, `obsdim` can be used to specify which dimension of   `data` denotes the observations. It can be specified in a   type-stable manner as a positional argument (see   `?LearnBase.ObsDim`), or more conveniently as a smart keyword   argument.

# Details

For `RandomObs` to work on some data structure, the type of the given variable `data` must implement the data container interface. See `?DataSubset` for more info.

# Author(s)

  * Christof Stocker (Github: https://github.com/Evizero)
  * Tom Breloff (Github: https://github.com/tbreloff)

# Examples

```julia
X, Y = MLDataUtils.load_iris()

# go over 500 randomly sampled observations in X
i = 0
for x in RandomObs(X, 500) # also: RandomObs(X, count = 500)
    @assert typeof(x) <: SubArray{Float64,1}
    @assert length(x) == 4
    i += 1
end
@assert i == 500

# if no count it provided the iterator will generate samples forever
for x in RandomObs(X)
    # this loop will never stop unless break is used
    if true; break; end
end

# also works for multiple data arguments (e.g. labeled data)
for (x,y) in RandomObs((X,Y), count = 100)
    @assert typeof(x) <: SubArray{Float64,1}
    @assert typeof(y) <: String
end
```

# see also

[`BalancedObs`](@ref), [`RandomBatches`](@ref), [`ObsView`](@ref), [`BatchView`](@ref), [`shuffleobs`](@ref), [`DataSubset`](@ref), [`BufferGetObs`](@ref)
