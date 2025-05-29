```
FixedVector{N,T} <: AbstractFixedVector{N,T}

FixedVector{N,T}(iter)
FixedVector{N}(iter)
FixedVector(iter)
```

`FixedVector{N,T}` は、型 `T` の要素を正確に `N` 個保持する不変ベクトル型です。（これは `StaticArrays.SVector` や `StaticVectors.Values` に類似しています。）サイズ `N` は任意の（小さな）正の整数であることができます。ただし、ビット整数およびハードウェア浮動小数点型の場合、通常は `N` を `2` の累乗とします。

要素型 `T` またはサイズ `N` が省略された場合、それらは引数として与えられたイテレータから決定されます。コンパイル時にこれが不可能な場合、パフォーマンスが低下します。（タプルの場合、要素型は `promote_type` を介して決定されます。）一般的な指針として、サイズは `Tuple` 引数の場合にのみ省略すべきです。

他にも [`MutableFixedVector`](@ref)、`Base.promote_type` を参照してください。
