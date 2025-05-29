```
cofactor_det(A::AbstractMatrix{T}) where {T}
```

`cofactor(A::AbstractMatrix{T})` computes the determinant of `A` using cofactor expansion (which can be slow). The return type of this method is a number of type `T`. The entries in `A` can be polynomials and that won't work with Julia's `det`.
