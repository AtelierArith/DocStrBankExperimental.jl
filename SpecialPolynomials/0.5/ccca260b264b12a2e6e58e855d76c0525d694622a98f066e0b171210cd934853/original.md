```
Bessel{α}
```

Implements the [Bessel](https://dlmf.nist.gov/18.34) polynomials, introduced by [Krall and Frink](https://www.ams.org/journals/tran/1949-065-01/S0002-9947-1949-0028473-1/S0002-9947-1949-0028473-1.pdf) (with `b=2`). The  case `a=2` corresponds to the [Bessel](https://en.wikipedia.org/wiki/Bessel_polynomials) polynomials of Wikipedia. The Bessel  polynomials are not orthogonal over  a domain of the real  line, rather over an arbitrary curve in the complex plane enclosing the  origin.  The weight  function is `ρ(x)=(2πi)^(-1)∑Γ(α)/Γ(α+n-1)(-β/x)^n`,   where `β=2`.

```jldoctest
julia> using Polynomials, SpecialPolynomials

julia> 𝐐 = Rational{Int}
Rational{Int64}

julia> x = variable(Polynomial{𝐐})
Polynomial(x)

julia> [basis(Bessel{3//2, 𝐐}, i)(x) for i in 0:5]
6-element Vector{Polynomial{Rational{Int64}, :x}}:
 Polynomial(1//1)
 Polynomial(1//1 + 3//4*x)
 Polynomial(1//1 + 5//2*x + 35//16*x^2)
 Polynomial(1//1 + 21//4*x + 189//16*x^2 + 693//64*x^3)
 Polynomial(1//1 + 9//1*x + 297//8*x^2 + 1287//16*x^3 + 19305//256*x^4)
 Polynomial(1//1 + 55//4*x + 715//8*x^2 + 10725//32*x^3 + 182325//256*x^4 + 692835//1024*x^5)
```
