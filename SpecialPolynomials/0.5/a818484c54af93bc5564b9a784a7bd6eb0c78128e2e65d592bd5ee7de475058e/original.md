```
Bernstein{N, T, X}
```

A [Bernstein  polynomial](https://en.wikipedia.org/wiki/Bernstein_polynomial) is a polynomial expressed in terms of Bernstein basic polynomials. For each degree, `𝐍`, this is a set of `𝐍+1` degree `𝐍` polynomials of the form: `β_{𝐍,ν} =  (ν choose 𝐍) x^ν  (1-x)^{𝐍-ν}`, `0 ≤ x ≤ 1.`

The `Bernstein{𝐍,T}` type represents a polynomial of degree `𝐍` or less with a linear combination of the basis vectors using coefficients of type `T`.

```jldoctest Bernstein
julia> using Polynomials, SpecialPolynomials

julia> p = basis(Bernstein{3},  2)
Bernstein(1⋅β₃,₂(x))

julia> convert(Polynomial, p)
Polynomial(3.0*x^2 - 3.0*x^3)
```

!!! note
    [StaticUnivariatePolynomials](https://github.com/tkoolen/StaticUnivariatePolynomials.jl) offers a  more  performant version.

