```
getlogpartition([ space = NaturalParametersSpace() ], ::Type{T}, [ conditioner ]) where { T <: Distribution }
```

A specific verion of `getlogpartition` defined particularly for distribution types from `Distributions.jl` package. Does not require an instance of the `ExponentialFamilyDistribution` and can be called directly with a specific distribution type instead. Optionally, accepts the `space` parameter, which defines the parameters space. For conditional exponential family distributions requires an extra `conditioner` argument.

See also: [`NaturalParametersSpace`](@ref), [`MeanParametersSpace`](@ref)
