```
FallingFactorial{T}
```

Construct  a  polynomial with   respect to the basis `x⁰̲,  x¹̲, x²̲, …` where `xⁱ̲ = x  ⋅  (x-1) ⋅  (x-2)  ⋯ (x-i+1)` is the falling Pochhammer  symbol.  See [Falling factorial](https://en.wikipedia.org/wiki/Falling_and_rising_factorials)  for several  facts about this  polynomial basis.

In [Koepf and Schmersau](https://arxiv.org/pdf/math/9703217.pdf) connection coefficients between the falling factorial polynomial system and classical discrete orthogonal polynomials are given.

## Examples

```jldoctest
julia> using Polynomials, SpecialPolynomials

julia> p = basis(FallingFactorial, 3)
Polynomials.MutableDensePolynomial(1.0⋅x³̲)

julia> x = variable(Polynomial)
Polynomial(1.0*x)

julia> p(x) ≈ x*(x-1)*(x-2)
true
```
