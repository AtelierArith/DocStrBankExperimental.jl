```
swizzle(v, indices...)
swizzle(T, v, indices...)
```

`v[i₁], v[i₂], ...` から構成される新しいオブジェクトを作成します。ここで `indices = (i₁, i₂, ...)` です。最初の引数として型が提供されると、結果は [`construct_swizzle`](@ref) を介してその型にラップされます。

デフォルトの型は `swizzle(v, indices...)` から導出され、単一のインデックスは `T = eltype(v)` を推論し、複数のインデックスは `T = typeof(v)` を推論します。静的サイズのベクトル（`StaticVector` および `SizedVector`）の場合、拡張が [StaticArraysCore](https://github.com/JuliaArrays/StaticArraysCore.jl) ベクトルを拡張し、結果を保持するために正しいサイズのものが使用されます。

参照: [`swizzle!`](@ref)
