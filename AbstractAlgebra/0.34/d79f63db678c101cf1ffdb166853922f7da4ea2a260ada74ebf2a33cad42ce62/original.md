```
tr(x::MatrixElem{T}) where T <: NCRingElement
```

Return the trace of the matrix $a$, i.e. the sum of the diagonal elements. We require the matrix to be square.

# Examples

```jldoctest; setup = :(using AbstractAlgebra)
julia> R, t = polynomial_ring(QQ, "t")
(Univariate polynomial ring in t over rationals, t)

julia> S = matrix_space(R, 3, 3)
Matrix space of 3 rows and 3 columns
  over univariate polynomial ring in t over rationals

julia> A = S([t + 1 t R(1); t^2 t t; R(-2) t + 2 t^2 + t + 1])
[t + 1       t             1]
[  t^2       t             t]
[   -2   t + 2   t^2 + t + 1]

julia> b = tr(A)
t^2 + 3*t + 2

```
