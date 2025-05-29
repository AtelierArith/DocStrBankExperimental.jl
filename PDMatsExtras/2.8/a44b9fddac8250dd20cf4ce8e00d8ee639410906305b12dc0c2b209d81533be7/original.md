```
WoodburyPDMat(
    A::AbstractMatrix{T}, D::Diagonal{T}, S::Diagonal{T},
) where {T<:Real}
```

Lazily represents matrices of the form

```julia
W = A * D * A' + S
```

`D` and `S` must have only non-negative entries.

Using this matrix type is a good idea if `size(A, 1) > size(A, 2)` as the structure in the matrix can be exploited to accelerate operations involving `W`'s inverse [1], such as `invquad`, and it's determinant [2], such as `logdet`.

You probably don't want to use this matrix type if `size(A, 1) < size(A, 2)`.

[1] - https://en.wikipedia.org/wiki/Woodbury*matrix*identity [2] - https://en.wikipedia.org/wiki/Matrix*determinant*lemma
