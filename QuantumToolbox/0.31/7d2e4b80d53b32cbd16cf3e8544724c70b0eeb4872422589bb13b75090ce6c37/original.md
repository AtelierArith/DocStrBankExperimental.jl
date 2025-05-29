```
dot(i::QuantumObject, A::AbstractQuantumObject j::QuantumObject)
matrix_element(i::QuantumObject, A::AbstractQuantumObject j::QuantumObject)
```

Compute the generalized dot product `dot(i, A*j)` between a [`AbstractQuantumObject`](@ref) and two [`QuantumObject`](@ref) (`i` and `j`), namely $\langle i | \hat{A} | j \rangle$.

Supports the following inputs:

  * `A` is in the type of [`Operator`](@ref), with `i` and `j` are both [`Ket`](@ref).
  * `A` is in the type of [`SuperOperator`](@ref), with `i` and `j` are both [`OperatorKet`](@ref)

!!! note
    `matrix_element(i, A, j)` is a synonym of `dot(i, A, j)`.

