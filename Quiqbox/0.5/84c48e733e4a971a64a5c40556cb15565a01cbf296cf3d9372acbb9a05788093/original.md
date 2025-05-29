```
genExponent(pb::ParamBox{T}) where {T<:AbstractFloat} -> ParamBox{T, :α}
```

Convert a [`ParamBox`](@ref) to the container of an exponent coefficient.
