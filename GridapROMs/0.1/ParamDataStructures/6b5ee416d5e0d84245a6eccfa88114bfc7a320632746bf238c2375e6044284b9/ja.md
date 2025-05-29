```
abstract type Snapshots{T,N,D,I<:AbstractDofMap{D},R<:AbstractRealization,A}
  <: AbstractSnapshots{T,N} end
```

型は、型 `R` の実現に関連付けられたエルタイプ `T` のパラメトリック抽象配列のコレクションを表します。`Snapshots` の任意のインスタンスの（空間的）エントリは、型 `I`:AbstractDofMap{`D`} のインデックスマップに従ってインデックス付けされ、`D` は空間次元をエンコードします。`AbstractParamArray` のサブタイプが配列の配列であるのに対し、`Snapshots` のサブタイプは数値の配列であることに注意してください。

サブタイプ:

  * [`SteadySnapshots`](@ref)
  * [`TransientSnapshots`](@ref)
