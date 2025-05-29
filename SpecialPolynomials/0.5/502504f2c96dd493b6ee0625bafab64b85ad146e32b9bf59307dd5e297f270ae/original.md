```
Hermite
```

The [Hermite](https://en.wikipedia.org/wiki/Hermite_polynomials) polynomials have two versions the physicists (`Hermite`  or  `H`) and the probablalists (`ChebyshevHermite` or  `Hₑ`). They are  related through  `Hᵢ(x) =  2^(i/2) Hₑᵢ(√2 x)`.

The Hermite   polynomials have weight  function `w(x)=exp(-x^2/2)` and domain the real line.

## Examples

```jldoctest
julia> using Polynomials,  SpecialPolynomials

julia> x = variable(Polynomial{Rational{Int}})
Polynomial(x)

julia> [basis(Hermite, i)(x) for i in 0:5]
6-element Vector{Polynomial{Float64, :x}}:
 Polynomial(1.0)
 Polynomial(2.0*x)
 Polynomial(-2.0 + 4.0*x^2)
 Polynomial(-12.0*x + 8.0*x^3)
 Polynomial(12.0 - 48.0*x^2 + 16.0*x^4)
 Polynomial(120.0*x - 160.0*x^3 + 32.0*x^5)

julia> [basis(ChebyshevHermite, i)(x) for i in 0:5]
6-element Vector{Polynomial{Float64, :x}}:
 Polynomial(1.0)
 Polynomial(1.0*x)
 Polynomial(-1.0 + 1.0*x^2)
 Polynomial(-3.0*x + 1.0*x^3)
 Polynomial(3.0 - 6.0*x^2 + 1.0*x^4)
 Polynomial(15.0*x - 10.0*x^3 + 1.0*x^5)
```

!!! note
    The Hermite family needs help, as the computed values for `Bn`,and,`Cn` are  both 0.

