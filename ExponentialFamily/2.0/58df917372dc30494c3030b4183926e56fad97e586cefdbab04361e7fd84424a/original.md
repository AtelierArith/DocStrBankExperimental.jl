```
NaturalToMean(::Type{T})
```

Return the transformation function that maps the parameters in the natural parameters space to the mean parameters space for a distribution of type `T`. The transformation function is of signature `(params_in_natural_space, [ conditioner ]) -> params_in_mean_space`.

See also: [`MeanToNatural`](@ref), [`NaturalParametersSpace`](@ref), [`MeanParametersSpace`](@ref), [`getmapping`](@ref)
