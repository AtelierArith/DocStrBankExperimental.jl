Gegenbauer{α, T <: Number}

Gegenbauer多項式は、領域`[-1,1]`上で重み関数`(1-x^2)^(α-1/2)`を持ちます。パラメータ`α`はコンストラクタで指定されます。これらは超球面多項式とも呼ばれます。レジェンドル多項式は、特化した形`Gegenbauer{1/2}`です。

```jldoctest
julia> using Polynomials, SpecialPolynomials

julia> p =  Gegenbauer{1/2}([1,2,3])
Gegenbauer{0.5}(1⋅Cᵅ₀(x) + 2⋅Cᵅ₁(x) + 3⋅Cᵅ₂(x))

julia> convert(Polynomial, p)
Polynomial(-0.5 + 2.0*x + 4.5*x^2)
```
