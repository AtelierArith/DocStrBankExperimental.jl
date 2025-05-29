```
AbstractBasis{T,N} <: AbstractArray{T,N}
```

型 `T` の要素を持つ基底を表すすべての型のスーパークラスです。基底は、型 `DenseLinear` の線形結合に必要です。

`AbstractBasis` のすべてのサブタイプは、[抽象配列インターフェース](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-array) を実装しなければなりません。与えられた基底 `b` に対して、`b[i]` は i 番目の基底要素です。基底要素からインデックスへのマッピングは `toindex` 関数を介して行われます。パラメータ `N == ndims(b)` は、基底 `b` の要素をインデックス付けするために使用されるインデックスの数を指定します。

関連項目として [`Basis`](@ref)、[`TensorBasis`](@ref)、[`toindex`](@ref)、`Base.ndims` があります。
