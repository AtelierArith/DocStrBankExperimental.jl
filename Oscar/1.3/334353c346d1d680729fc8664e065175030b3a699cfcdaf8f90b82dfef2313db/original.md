```
is_hermitian(B::MatElem{T}) where T <: FinFieldElem
```

Return whether the matrix `B` is hermitian, i.e. `B = conjugate_transpose(B)`. Return `false` if `B` is not a square matrix, or the field has not even degree.
