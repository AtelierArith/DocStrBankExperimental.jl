```
SparsePolynomial{T, X}(coeffs::Dict{Int,T})
```

辞書を使用して非ゼロ係数を保持する標準基底の多項式。高次の多項式の場合、これは有利かもしれません。

# 例:

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

julia> p = Polynomials.basis(P, 10^9) - Polynomials.basis(P,0) # これは P(Dict(0=>-1, 10^9=>1)) でもあります
SparsePolynomial(-1.0 + 1.0*x^1000000000)

julia> p(1)
0.0
```

!!! 注     `SparsePolynomial` は `MutableSparsePolynomial{StandardBasis}` のエイリアスです。
