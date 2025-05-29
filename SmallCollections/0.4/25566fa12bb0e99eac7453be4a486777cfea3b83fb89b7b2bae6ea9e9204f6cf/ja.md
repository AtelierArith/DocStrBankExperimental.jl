```
MutableSmallVector{N,T} <: AbstractSmallVector{N,T}

MutableSmallVector{N,T}()
MutableSmallVector{N,T}(iter)
MutableSmallVector{N}(iter)
MutableSmallVector(v::PackedVector{T})
MutableSmallVector(v::AbstractSmallVector)

MutableSmallVector{N,T}(undef, n::Integer)
```

`MutableSmallVector{N,T}` は、型 `T` の要素を最大 `N` 個保持できる可変ベクトル型です。これは `SmallVector{N,T}` の可変版です。

個々のベクトル要素を設定すること（`setindex!` を介して）は、`isbits` 要素型に対してのみサポートされています。

特別な形式 `MutableSmallVector{N,T}(undef, n)` は、長さ `n` の未初期化ベクトルを返します。

他にも [`SmallVector`](@ref)、`Base.isbitstype` を参照してください。
