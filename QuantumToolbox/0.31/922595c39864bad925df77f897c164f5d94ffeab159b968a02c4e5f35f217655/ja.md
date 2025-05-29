```
matrix_element(i::QuantumObject, A::QuantumObject j::QuantumObject)
```

三つの [`QuantumObject`](@ref) の間の一般化ドット積 `dot(i, A*j)` を計算します: $\langle i | \hat{A} | j \rangle$

この関数は `dot(i, A, j)` と同じであることに注意してください。

以下の入力をサポートしています:

  * `A` は [`Operator`](@ref) の型であり、`i` と `j` は両方とも [`Ket`](@ref) です。
  * `A` は [`SuperOperator`](@ref) の型であり、`i` と `j` は両方とも [`OperatorKet`](@ref) です。
