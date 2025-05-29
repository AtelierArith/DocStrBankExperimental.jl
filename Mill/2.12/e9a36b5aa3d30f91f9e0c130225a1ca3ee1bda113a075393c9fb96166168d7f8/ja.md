```
AlignedBags{T <: Integer} <: AbstractBags{T}
```

[`AlignedBags`](@ref) 構造体は、1つ以上の `UnitRange{T}` 内のバッグのインスタンスのインデックスを格納します。これは、すべてのバッグのインスタンスが1つの連続したブロックに格納されている場合にのみ可能です。

参照: [`ScatteredBags`](@ref).
