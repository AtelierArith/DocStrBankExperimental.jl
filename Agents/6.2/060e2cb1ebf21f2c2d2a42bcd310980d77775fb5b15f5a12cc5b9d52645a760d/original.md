```
ContinuousAgent{D,T} <: AbstractAgent
```

The minimal agent struct for usage with `D`-dimensional [`ContinuousSpace`](@ref). It has the additional fields `pos::SVector{D,T}, vel::SVector{D,T}` where `T` can be any `AbstractFloat` type. See also [`@agent`](@ref).
