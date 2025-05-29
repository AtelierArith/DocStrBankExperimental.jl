```
genContraction(pb::ParamBox{T}) where {T<:AbstractFloat} -> ParamBox{T, :d}
```

Convert a [`ParamBox`](@ref) to an exponent coefficient parameter.
