```
matrix_element(i::QuantumObject, A::QuantumObject j::QuantumObject)
```

Compute the generalized dot product `dot(i, A*j)` between three [`QuantumObject`](@ref): $\langle i | \hat{A} | j \rangle$

Note that this function is same as `dot(i, A, j)`

Supports the following inputs:

  * `A` is in the type of [`Operator`](@ref), with `i` and `j` are both [`Ket`](@ref).
  * `A` is in the type of [`SuperOperator`](@ref), with `i` and `j` are both [`OperatorKet`](@ref)
