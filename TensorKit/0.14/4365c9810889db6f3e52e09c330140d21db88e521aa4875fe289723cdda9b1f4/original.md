```
storagetype(t::AbstractTensorMap) -> Type{A<:AbstractVector}
storagetype(T::Type{<:AbstractTensorMap}) -> Type{A<:AbstractVector}
```

Return the type of vector that stores the data of a tensor.
