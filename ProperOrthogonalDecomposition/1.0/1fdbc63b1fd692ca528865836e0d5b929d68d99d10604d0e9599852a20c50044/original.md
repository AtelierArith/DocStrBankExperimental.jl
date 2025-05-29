```
function modeConvergence!(loadFun, PODfun, stops::AbstractArray{<: AbstractRange}, numModes::Int)
```

Same as `modeConvergence(X::AbstractArray, PODfun, stops::AbstractArray{<: AbstractRange}, numModes::Int)`  but here the data is reloaded for each comparision so that an inplace POD method can be used to reduce maximum memory usage.
