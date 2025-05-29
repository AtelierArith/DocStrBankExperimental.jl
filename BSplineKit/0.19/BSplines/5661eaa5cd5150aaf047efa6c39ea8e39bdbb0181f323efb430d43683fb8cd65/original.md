```
evaluate!(b::AbstractVector, B::BSplineBasis, i::Integer,
          x::AbstractVector, args...)
```

Evaluate i-th basis function at positions `x` and write result to `b`.

See also [`evaluate`](@ref).
