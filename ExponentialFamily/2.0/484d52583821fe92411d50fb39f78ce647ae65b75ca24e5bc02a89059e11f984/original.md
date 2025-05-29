```
NaturalParametersSpace
```

Specifies the natural parameters space `η` as the desired parameters space. Some functions (such as `logpartition` or `fisherinformation`) accept an additional `space` parameter to disambiguate the desired parameters space.  Use `map(NaturalParametersSpace() => MeanParametersSpace(), T, parameters, conditioner)` to map the `parameters` and the `conditioner` of a distribution of type `T` from the natural parametrization to the corresponding mean parametrization.

See also: [`MeanParametersSpace`](@ref), [`getmapping`](@ref), [`NaturalToMean`](@ref), [`MeanToNatural`](@ref)
