```
is_invertible(A::MatrixElem{T}) where {T <: RingElement}
```

Return true if a given square matrix is invertible, false otherwise. If the inverse should also be computed, use `is_invertible_with_inverse`.
