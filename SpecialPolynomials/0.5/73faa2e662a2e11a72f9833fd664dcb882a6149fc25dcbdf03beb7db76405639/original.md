```
Chebyshev{<:Number}(coeffs::AbstractVector, var=:x)
```

[Chebyshev](https://en.wikipedia.org/wiki/Chebyshev_polynomials) polynomial of the first kind. These have domain $(-1,1)$ and weight function $1/\sqrt{1-x^2}$.

A polynomial is constructed from its coefficients `a`, lowest order first, optionally in terms of the given variable `x`. `x` can be a character, symbol, or string.

# Examples

```jldoctest
julia> using Polynomials, SpecialPolynomials

julia> Chebyshev([1, 0, 3, 4])
Chebyshev(1⋅T₀(x) + 3⋅T₂(x) + 4⋅T₃(x))

julia> Chebyshev([1, 2, 3, 0], :s)
Chebyshev(1⋅T₀(s) + 2⋅T₁(s) + 3⋅T₂(s))

julia> one(Chebyshev)
Chebyshev(1.0⋅T₀(x))
```

!!! note
    This is copied from the `ChebyshevT` example from the `Polynomials` package by Miles Lucas.


!!! note
    The sample chapter available online of [Numerical Methods for Special Functions" by Amparo Gil, Javier Segura, and Nico Temme](https://archive.siam.org/books/ot99/OT99SampleChapter.pdf) gives a very nice overview of these polynomials.

