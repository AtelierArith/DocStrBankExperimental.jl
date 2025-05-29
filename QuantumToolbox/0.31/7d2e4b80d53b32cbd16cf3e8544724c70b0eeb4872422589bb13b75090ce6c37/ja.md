```
dot(i::QuantumObject, A::AbstractQuantumObject j::QuantumObject)
matrix_element(i::QuantumObject, A::AbstractQuantumObject j::QuantumObject)
```

一般化ドット積 `dot(i, A*j)` を計算します。これは [`AbstractQuantumObject`](@ref) と二つの [`QuantumObject`](@ref) (`i` と `j`) の間のもので、具体的には $\langle i | \hat{A} | j \rangle$ です。

以下の入力をサポートします：

  * `A` は [`Operator`](@ref) の型で、`i` と `j` は両方とも [`Ket`](@ref) です。
  * `A` は [`SuperOperator`](@ref) の型で、`i` と `j` は両方とも [`OperatorKet`](@ref) です。

!!! note
    `matrix_element(i, A, j)` は `dot(i, A, j)` の同義語です。

