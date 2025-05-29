```
RotatingTimeArray{T<:RotatingTimeValue,N,C,I} <: AbstractArray{T,N}
```

Array type for [`RotatingTimeValue`](@ref)s that stores the field values `rotation` and `time` in two arrays for efficiency. The two arrays that hold the field values for all elements can be accessed as properties.
