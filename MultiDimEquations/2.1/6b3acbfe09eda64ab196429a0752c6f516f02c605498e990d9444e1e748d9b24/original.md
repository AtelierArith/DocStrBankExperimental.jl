```
getSafe(idxtable,indices,missingValue=missing)
```

Return the value stored in a NDSParse table or missingValue if the specified keys are not present.

# Arguments

  * `idxtable`: The NDSParse table to lookup
  * `indices`: A tuple with the indices to use (`:` is supported)
  * `missingValue`: The value to return if the specified keys are not found

# Examples

```julia
julia> volBlackForest2014  = getSafe(forestVolumes,("BlackForest",2014),0.0)
```
