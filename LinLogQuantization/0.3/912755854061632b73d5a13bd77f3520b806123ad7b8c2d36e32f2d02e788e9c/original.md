```
LogQuantArray(::Type{TUInt},A::AbstractArray{T,N};dims::Int) where {TUInt<:Unsigned,T,N}
```

Logarithmic quantization independently for every element along dimension `dims` in array `A`.

# Returns

  * a Vector{LogQuantArray}.
