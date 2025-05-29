Companion(v::Union{AbstractVector,Polynomial})::AbstractMatrix

Construct a lazy [`companion` matrix](https://en.wikipedia.org/wiki/Companion_matrix) from the coefficients of its characteristic (monic) polynomial.

The matrix is `n × n` for a vector input of length `n` or an input `Polynomial` of degree `n`, but the storage here is only `O(n)`. This version puts the coefficients along the last column of the matrix. Some texts put the coefficients along the first row, the transpose of the convention used here.

This type has efficient methods for `mul!` and `inv`.

```jldoctest
julia> A = Companion([3,2,1])
3×3 Companion{Int64}:
 0  0  -3
 1  0  -2
 0  1  -1
```

Also, directly from a polynomial:

```jldoctest
julia> using Polynomials

julia> P = Polynomial(2:5)
Polynomial(2 + 3*x + 4*x^2 + 5*x^3)

julia> C = Companion(P)
3×3 Companion{Float64}:
 0.0  0.0  -0.4
 1.0  0.0  -0.6
 0.0  1.0  -0.8
```
