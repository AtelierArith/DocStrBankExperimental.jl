```
FactoredPolynomial{T,X}
```

A polynomial type that stores its data in a dictionary whose keys are the roots and whose values are the respective multiplicities along with a leading coefficient.

The structure is utilized for scalar multiplication, polynomial multiplication and powers, the finding of roots, and the identification of a greatest common divisor. For other operations, say addition, the operation is done after converting to the `Polynomial` type then converting back. (This requires the identification of the roots, so is subject to numeric issues.)

## Examples

```jldoctest factored_polynomial
julia> using Polynomials

julia> p = FactoredPolynomial(Dict([0=>1, 1=>2, 3=>4]))
FactoredPolynomial(x * (x - 3)⁴ * (x - 1)²)

julia> q = fromroots(FactoredPolynomial, [0,1,2,3])
FactoredPolynomial((x - 3) * x * (x - 2) * (x - 1))

julia> p*q
FactoredPolynomial(x² * (x - 3)⁵ * (x - 1)³ * (x - 2))

julia> p^1000
FactoredPolynomial(x¹⁰⁰⁰ * (x - 3)⁴⁰⁰⁰ * (x - 1)²⁰⁰⁰)

julia> gcd(p,q)
FactoredPolynomial(x * (x - 3) * (x - 1))

julia> p = Polynomial([24, -50, 35, -10, 1])
Polynomial(24 - 50*x + 35*x^2 - 10*x^3 + x^4)

julia> q = convert(FactoredPolynomial, p) # noisy form of `factor`:
FactoredPolynomial((x - 4.0000000000000036) * (x - 1.0000000000000002) * (x - 2.9999999999999942) * (x - 2.0000000000000018))

julia> map(x->round(x, digits=12), q) # map works over factors and leading coefficient -- not coefficients in the standard basis
FactoredPolynomial((x - 4.0) * (x - 2.0) * (x - 3.0) * (x - 1.0))
```
