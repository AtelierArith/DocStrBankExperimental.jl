```
FactoredPolynomial{T,X}
```

データを根をキーとし、それぞれの重複度と先頭係数を値とする辞書に格納する多項式型です。

この構造は、スカラー乗算、多項式乗算と累乗、根の発見、および最大公約数の特定に利用されます。他の演算、例えば加算は、`Polynomial`型に変換してから戻すことで行われます（これは根の特定を必要とするため、数値的な問題の影響を受けます）。

## 例

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
