```
normalize(A::QuantumObject, p::Real)
unit(A::QuantumObject, p::Real)
```

返された正規化された [`QuantumObject`](@ref) は、その `p`-ノルムが単位に等しくなるようにします。すなわち、`norm(A, p) == 1` です。

以下のタイプの [`QuantumObject`](@ref) をサポートします：

  * `A` が [`Ket`](@ref) または [`Bra`](@ref) の場合、デフォルトの `p = 2`
  * `A` が [`Operator`](@ref) の場合、デフォルトの `p = 1`

!!! note
    `unit` は `normalize` の同義語です。


また、異なるタイプの [`QuantumObject`](@ref) に対する定義については [`norm`](@ref) を参照してください。
