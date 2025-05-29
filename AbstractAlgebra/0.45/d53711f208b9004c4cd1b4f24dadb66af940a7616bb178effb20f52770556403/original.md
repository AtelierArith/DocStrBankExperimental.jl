```
det(M::MatrixElem{T}) where {T <: RingElement}
```

Return the determinant of the matrix $M$. We assume $M$ is square.

# Examples

```jldoctest
julia> R, x = polynomial_ring(QQ, :x)
(Univariate polynomial ring in x over rationals, x)

julia> A = R[x 1; 1 x^2];

julia> d = det(A)
x^3 - 1
```
