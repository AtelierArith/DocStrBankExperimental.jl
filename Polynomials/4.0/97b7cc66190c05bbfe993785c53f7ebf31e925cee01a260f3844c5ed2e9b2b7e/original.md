```
ChebyshevT{T, X}(coeffs::AbstractVector)
```

Chebyshev polynomial of the first kind.

Construct a polynomial from its coefficients `coeffs`, lowest order first, optionally in terms of the given variable `var`, which can be a character, symbol, or string.

!!! note
    `ChebyshevT` is not axis-aware, and it treats `coeffs` simply as a list of coefficients with the first index always corresponding to the coefficient of `T_0(x)`.


# Examples

```jldoctest ChebyshevT
julia> using Polynomials

julia> p = ChebyshevT([1, 0, 3, 4])
ChebyshevT(1⋅T_0(x) + 3⋅T_2(x) + 4⋅T_3(x))

julia> ChebyshevT([1, 2, 3, 0], :s)
ChebyshevT(1⋅T_0(s) + 2⋅T_1(s) + 3⋅T_2(s))

julia> one(ChebyshevT)
ChebyshevT(1.0⋅T_0(x))

julia> p(0.5)
-4.5

julia> Polynomials.evalpoly(5.0, p, false) # bypasses the domain check done in p(5.0)
2088.0
```

The latter shows how to evaluate a `ChebyshevT` polynomial outside of its domain, which is `[-1,1]`. (For newer versions of `Julia`, `evalpoly` is an exported function from Base with methods extended in this package, so the module qualification is unnecessary.

!!! note
    The Chebyshev polynomials are also implemented in `ApproxFun`, `ClassicalOrthogonalPolynomials.jl`, `FastTransforms.jl`, and `SpecialPolynomials.jl`.

