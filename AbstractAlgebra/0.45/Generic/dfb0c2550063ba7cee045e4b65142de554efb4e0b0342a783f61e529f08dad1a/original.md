```
dense_matrix_type(::Type{T}) where T<:NCRingElement
dense_matrix_type(::T) where T<:NCRingElement
dense_matrix_type(::Type{S}) where S<:NCRing
dense_matrix_type(::S) where S<:NCRing
```

Return the type of matrices with coefficients of type `T` respectively `elem_type(S)`.

Implementations of the ring interface only need to provide a method for the argument a subtype of `NCRingElement`; the other variants are implemented by calling that method.
