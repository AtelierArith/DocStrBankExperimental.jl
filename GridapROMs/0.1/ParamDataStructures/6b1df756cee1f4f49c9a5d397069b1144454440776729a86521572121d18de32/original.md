```
struct BlockParamArray{T,N,A<:AbstractArray{<:AbstractParamArray{T,N},N},B<:NTuple{N,AbstractUnitRange{Int}}} <: ParamArray{T,N}
  data::A
  axes::B
end
```

Is to a [`ParamArray`](@ref) as a `BlockArray` is to a regular `AbstractArray`
