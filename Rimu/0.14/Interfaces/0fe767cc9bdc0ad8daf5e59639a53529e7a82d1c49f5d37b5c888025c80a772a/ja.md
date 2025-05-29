```
LOStructure(op::AbstractHamiltonian)
LOStructure(typeof(op))
```

線形演算子 `op` の構造に関する情報を返します。`LOStructure` は、計算を簡素化または加速する可能性のある線形演算子 `op` の対称性やその他の特性を指定するためのトレイトとして使用されます。実装されたインスタンスは次のとおりです：

  * `IsDiagonal()`: 演算子は対角行列です。
  * `IsHermitian()`: 演算子は複素数でエルミートか、実数で対称です。
  * `AdjointKnown()`: 演算子はエルミートではありませんが、その [`adjoint`](@ref Main.Hamiltonians.adjoint) が実装されています。
  * `AdjointUnknown()`: この演算子の [`adjoint`](@ref Main.Hamiltonians.adjoint) は実装されていません。

[`AbstractHamiltonian`](@ref) インターフェースの一部です。

新しい線形演算子型のためにこのトレイトを定義するには、`LOStructure(::Type{<:MyNewLOType}) = …` のメソッドを定義します。
