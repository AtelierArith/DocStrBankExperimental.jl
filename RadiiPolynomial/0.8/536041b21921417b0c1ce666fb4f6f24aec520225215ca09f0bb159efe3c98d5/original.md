```
evaluate!(c::Union{AbstractVector,Sequence}, a::Sequence, x)
```

Evaluate `a` at `x`. The result is stored in `c` by overwriting it.

See also: [`(::Sequence)(::Any, ::Vararg)`](@ref), [`evaluate`](@ref), [`Evaluation`](@ref), [`*(::Evaluation, ::Sequence)`](@ref) and [`(::Evaluation)(::Sequence)`](@ref).
