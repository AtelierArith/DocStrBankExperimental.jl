```
struct BlockParamArray{T,N,A<:AbstractArray{<:AbstractParamArray{T,N},N},B<:NTuple{N,AbstractUnitRange{Int}}} <: ParamArray{T,N}
  data::A
  axes::B
end
```

は、`BlockArray`が通常の`AbstractArray`に対するのと同様に、[`ParamArray`](@ref)に対するものです。
