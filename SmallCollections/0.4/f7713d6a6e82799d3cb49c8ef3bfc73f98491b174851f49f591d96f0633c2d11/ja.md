```
MutableFixedVector{N,T} <: AbstractFixedVector{N,T}

MutableFixedVector{N,T}(iter)
MutableFixedVector{N}(iter)
MutableFixedVector(iter)

MutableFixedVector{N,T}(undef)
```

`MutableFixedVector{N,T}` は、型 `T` の要素を正確に `N` 個保持する可変ベクトル型です。（これは `StaticArrays.MVector` および `StaticVectors.Variables` に類似しています。）サイズ `N` は任意の（小さな）正の整数であることができます。ただし、ビット整数およびハードウェア浮動小数点型の場合、通常は `N` を `2` の累乗とします。

要素型 `T` またはサイズ `N` が省略された場合、それらは引数として与えられたイテレータから決定されます。コンパイル時にこれが不可能な場合、パフォーマンスは低下します。一般的な指針として、サイズは `Tuple` 引数の場合にのみ省略すべきです。

個々のベクトル要素を設定すること（`setindex!` を介して）は、`isbits` 要素型に対してのみサポートされています。

特別な形式 `MutableFixedVector{N,T}(undef)` は、初期化されていないベクトルを返します。

関連情報として [`FixedVector`](@ref)、`Base.isbitstype` を参照してください。
