```
spacetype(::AbstractTensorMap) -> Type{S<:IndexSpace}
spacetype(::Type{<:AbstractTensorMap}) -> Type{S<:IndexSpace}
```

テンソルの基本空間 `S` の型を返します。
