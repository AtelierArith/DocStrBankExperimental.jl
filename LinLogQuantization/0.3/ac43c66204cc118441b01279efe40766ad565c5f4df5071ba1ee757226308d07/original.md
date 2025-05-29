```
LogQuantArray(::Type{TUInt},A::AbstractArray{T,N},dim::Int) where {TUInt,T,N}
```

Logarithmic quantization independently for every element along dimension dim in array A.

# Arguments

  * `TUInt`: the type of the quantised array
  * `A`: the array to quantise
  * `dim`: the dimension along which to quantise

# Returns

  * a Vector{LogQuantArray} with the quantised array and the minimum and maximum of the original range.
