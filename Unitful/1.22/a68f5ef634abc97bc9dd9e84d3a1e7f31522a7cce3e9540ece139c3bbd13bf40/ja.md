```
struct Quantity{T,D,U} <: AbstractQuantity{T,D,U}
```

[`Unitful.AbstractQuantity`](@ref) の具体的なサブタイプです。

型パラメータ `T` は数値のバックタイプを表します。型パラメータ `D ::` [`Unitful.Dimensions`](@ref) と `U <:` [`Unitful.Units`](@ref) です。
