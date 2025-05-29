```
impulse(var::VARProcess, ε0::AbstractVecOrMat, nhorz::Integer; kwargs...)
impulse(var::VARProcess, ishock::Union{Integer, AbstractRange}, nhorz::Integer; kwargs...)
```

Same as [`impulse!`](@ref), but allocates an array for storing the results. The number of horizons needs to be specified explicitly with `nhorz`.
