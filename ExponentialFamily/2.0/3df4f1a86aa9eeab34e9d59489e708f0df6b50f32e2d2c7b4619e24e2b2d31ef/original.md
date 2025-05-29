```
MeanParametersSpace
```

Specifies the mean parameters space `θ` as the desired parameters space. Some functions (such as `logpartition` or `fisherinformation`) accept an additional `space` parameter to disambiguate the desired parameters space.  Use `map(MeanParametersSpace() => NaturalParametersSpace(), T, parameters, conditioner)` to map the `parameters` and the `conditioner` of a distribution of type `T` from the mean parametrization to the corresponding natural parametrization.

See also: [`NaturalParametersSpace`](@ref), [`getmapping`](@ref), [`NaturalToMean`](@ref), [`MeanToNatural`](@ref)
