```
SparsePolynomial{T, X}(coeffs::Dict{Int,T})
```

Polynomials in the standard basis backed by a dictionary holding the non-zero coefficients. For polynomials of high degree, this might be advantageous.

# Examples:

```jldoctest
julia> using Polynomials

julia> P = SparsePolynomial;

julia> p, q = P([1,2,3]), P([4,3,2,1])
(SparsePolynomial(1 + 2*x + 3*x^2), SparsePolynomial(4 + 3*x + 2*x^2 + x^3))

julia> p + q
SparsePolynomial(5 + 5*x + 5*x^2 + x^3)

julia> p * q
SparsePolynomial(4 + 11*x + 20*x^2 + 14*x^3 + 8*x^4 + 3*x^5)

julia> p + 1
SparsePolynomial(2 + 2*x + 3*x^2)

julia> q * 2
SparsePolynomial(8 + 6*x + 4*x^2 + 2*x^3)

julia> p = Polynomials.basis(P, 10^9) - Polynomials.basis(P,0) # also P(Dict(0=>-1, 10^9=>1))
SparsePolynomial(-1.0 + 1.0*x^1000000000)

julia> p(1)
0.0
```

!!! note
    `SparsePolynomial` is an alias for `MutableSparsePolynomial{StandardBasis}`.

