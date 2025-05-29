```
storagetype(t::AbstractTensorMap) -> Type{A<:AbstractVector}
storagetype(T::Type{<:AbstractTensorMap}) -> Type{A<:AbstractVector}
```

テンソルのデータを格納するベクトルの型を返します。
