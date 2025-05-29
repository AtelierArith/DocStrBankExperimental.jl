```
FallingFactorial{T}
```

基底 `x⁰̲,  x¹̲, x²̲, …` に関して多項式を構築します。ここで `xⁱ̲ = x  ⋅  (x-1) ⋅  (x-2)  ⋯ (x-i+1)` は降下ポッホマーハ記号です。この多項式基底に関するいくつかの事実については、[Falling factorial](https://en.wikipedia.org/wiki/Falling_and_rising_factorials) を参照してください。

[Koepf and Schmersau](https://arxiv.org/pdf/math/9703217.pdf) では、降下多項式系と古典的離散直交多項式との間の接続係数が与えられています。

## 例

```jldoctest
julia> using Polynomials, SpecialPolynomials

julia> p = basis(FallingFactorial, 3)
Polynomials.MutableDensePolynomial(1.0⋅x³̲)

julia> x = variable(Polynomial)
Polynomial(1.0*x)

julia> p(x) ≈ x*(x-1)*(x-2)
true
```
