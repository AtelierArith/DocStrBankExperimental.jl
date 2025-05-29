```
MeanToNatural(::Type{T})
```

Return the transformation function that maps the parameters in the mean parameters space to the natural parameters space for a distribution of type `T`. The transformation function is of signature `(params_in_mean_space, [ conditioner ]) -> params_in_natural_space`.

See also: [`NaturalToMean`](@ref), [`NaturalParametersSpace`](@ref), [`MeanParametersSpace`](@ref), [`getmapping`](@ref)
