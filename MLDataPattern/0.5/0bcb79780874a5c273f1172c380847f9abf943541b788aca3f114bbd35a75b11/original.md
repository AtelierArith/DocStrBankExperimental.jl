```
BalancedObs([f], data, [count], [obsdim])
```

# Description

Create an iterator that generates `count` randomly sampled observations from `data`. In the case `count` is not provided, it will generate random samples indefinitely.

In contrast to [`RandomObs`](@ref), `BalancedObs` expects `data` to be a labeled data container. It uses the label distribution of `data` to make sure every label has an equal probability to be sampled from.

# Arguments

  * **`f`** : Optional. A function that should be applied to each   observation individually in order to extract or compute the   target for that observation. This function is only used once   during construction to determine which label each observation   belongs to.
  * **`data`** : The object describing the dataset. Can be of any   type as long as it implements [`getobs`](@ref),   [`nobs`](@ref), and optionally [`gettargets`](@ref) (see   Details for more information).
  * **`count`** : Optional. The number of randomly sampled   observations that the iterator will generate before stopping.   If omitted, the iterator will generate randomly sampled   observations forever.
  * **`obsdim`** : Optional. If it makes sense for the type of   `data`, `obsdim` can be used to specify which dimension of   `data` denotes the observations. It can be specified in a   type-stable manner as a positional argument (see   `?LearnBase.ObsDim`), or more conveniently as a smart keyword   argument.

# Details

For `BalancedObs` to work on some data structure, the type of the given variable `data` must implement the labeled data container interface. See `?DataSubset` for more info.

# Author(s)

  * Christof Stocker (Github: https://github.com/Evizero)

# Examples

```julia
# load first 55 observations of the iris data as example
# - 50 observations for "setosa"
# -  5 observations for "versicolor"
X, Y = MLDataUtils.load_iris(55)

# go over 100 balanced samples observations in X
num_versicolor = 0
for (x,y) in BalancedObs((X,Y), 100) # also: BalancedObs((X,Y), count = 100)
    @assert typeof(x) <: SubArray{Float64,1}
    @assert length(x) == 4
    # count how many times we sample a versicolor observation
    num_versicolor += y[] == "versicolor" ? 1 : 0
end
println(num_versicolor) # around 50

# if no count it provided the iterator will generate samples forever
for (x,y) in BalancedObs((X,Y))
    # this loop will never stop unless break is used
    if true; break; end
end
```

# see also

[`RandomObs`](@ref), [`targets`](@ref), [`RandomBatches`](@ref), [`ObsView`](@ref), [`BatchView`](@ref), [`shuffleobs`](@ref), [`DataSubset`](@ref), [`BufferGetObs`](@ref)
