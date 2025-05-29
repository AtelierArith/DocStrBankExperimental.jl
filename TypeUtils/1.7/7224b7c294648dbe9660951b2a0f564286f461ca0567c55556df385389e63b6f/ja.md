```
new_array(T, inds...) -> A
new_array(T, (inds...,)) -> A
```

要素型 `T` と `inds...` で定義された形状を持つ新しい配列を作成します。`inds...` は配列の次元の長さやインデックス範囲のリストです。形状はタプルとしても指定できます。

`inds...` に `Base.OneTo` 以外のインデックス範囲が含まれている場合、`OffsetArray{T}` が返されます。それ以外の場合は `Array{T}` が返されます。前者の場合、`OffsetArrays` パッケージがロードされていないと例外がスローされます。

また、[`as_array_shape`](@ref)、[`as_array_axes`](@ref)、および [`as_array_size`](@ref) も参照してください。
