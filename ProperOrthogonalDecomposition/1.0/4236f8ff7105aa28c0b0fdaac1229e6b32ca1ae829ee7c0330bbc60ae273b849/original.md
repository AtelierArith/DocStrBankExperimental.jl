```
function modeConvergence(X::AbstractArray, PODfun, stops::AbstractArray{<: AbstractRange}, numModes::Int)
```

Modal convergence check based on l2-norm of modes. The array `stops` contains the ranges to investigate where `stops[end]` is used as the reference modes. The `numModes` largest modes are compared to reduce the computational time. The function used to POD the data is supplied through `PODfun`
