```
getNodeElems(::Val{:DAT}, pathname::ST; FT::Type{T}=Precision.FT, meshUnit = :m) where {ST <: AbstractString,T<:AbstractFloat}
```

读取 `.dat` 格式的自定义项目文件。
