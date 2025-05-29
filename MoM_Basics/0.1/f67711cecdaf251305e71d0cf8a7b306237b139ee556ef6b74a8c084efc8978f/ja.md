```
getNodeElems(::Val{:DAT}, pathname::ST; FT::Type{T}=Precision.FT, meshUnit = :m) where {ST <: AbstractString,T<:AbstractFloat}
```

`.dat` 形式のカスタムプロジェクトファイルを読み取ります。
