```
normalize!(A::QuantumObject, p::Real)
```

[`QuantumObject`](@ref) をインプレースで正規化して、その `p`-ノルムが1になるようにします。すなわち、`norm(A, p) == 1` です。

以下のタイプの [`QuantumObject`](@ref) に対するサポート：

  * `A` が [`Ket`](@ref) または [`Bra`](@ref) の場合、デフォルトの `p = 2`
  * `A` が [`Operator`](@ref) の場合、デフォルトの `p = 1`

また、異なるタイプの [`QuantumObject`](@ref) に対する定義については [`norm`](@ref) を参照してください。
