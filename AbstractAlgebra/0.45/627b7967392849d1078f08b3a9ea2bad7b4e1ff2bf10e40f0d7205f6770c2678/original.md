```
transpose(x::MatrixElem{T}) where T <: NCRingElement
```

Return the transpose of the given matrix.

# Examples

```jldoctest
julia> R, t = polynomial_ring(QQ, :t)
(Univariate polynomial ring in t over rationals, t)

julia> S = matrix_space(R, 3, 3)
Matrix space of 3 rows and 3 columns
  over univariate polynomial ring in t over rationals

julia> A = S([t + 1 t R(1); t^2 t t; R(-2) t + 2 t^2 + t + 1])
[t + 1       t             1]
[  t^2       t             t]
[   -2   t + 2   t^2 + t + 1]

julia> B = transpose(A)
[t + 1   t^2            -2]
[    t     t         t + 2]
[    1     t   t^2 + t + 1]

```
