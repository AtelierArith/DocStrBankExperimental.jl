```
abstract type AbstractField{T,N,L} <: AbstractArray{T,N}
```

Abstract type representing a field with data type `T`, number of dimensions `N`, location `L` where the field should be defined on.

See also: abstract type [`ConstantField`](@ref)
