```
AbstractCapacityVector{T} <: AbstractVector{T}
```

`AbstractCapacityVector` は、このモジュールによって提供される可変長ベクトル型のスーパークラスです。現在、これらは `AbstractSmallVector` と `PackedVector` です。どちらも、事前に定義された最大容量までの可変数の要素を保持できます。要素型 `T` が具体的である場合、イミュータブルベクトル型はメモリを割り当てません。

参照: [`AbstractSmallVector`](@ref), [`PackedVector`](@ref).
