```
Bessel{α}
```

[Bessel](https://dlmf.nist.gov/18.34) 多項式を実装します。これは [Krall and Frink](https://www.ams.org/journals/tran/1949-065-01/S0002-9947-1949-0028473-1/S0002-9947-1949-0028473-1.pdf) によって導入されました（`b=2` の場合）。`a=2` の場合は、Wikipedia の [Bessel](https://en.wikipedia.org/wiki/Bessel_polynomials) 多項式に対応します。Bessel 多項式は実数直線の領域上では直交しませんが、原点を囲む複素平面の任意の曲線上では直交します。重み関数は `ρ(x)=(2πi)^(-1)∑Γ(α)/Γ(α+n-1)(-β/x)^n` であり、ここで `β=2` です。

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
