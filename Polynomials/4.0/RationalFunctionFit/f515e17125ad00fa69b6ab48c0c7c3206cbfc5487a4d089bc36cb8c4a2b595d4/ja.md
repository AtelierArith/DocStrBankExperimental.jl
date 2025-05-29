```
fit(::Type{RationalFunction}, r::Polynomial, m, n; var=:x)
```

Pade近似を`r`にフィットさせます（`Polynomials.pade_fit`のドキュメントを参照）。

例:

```julia-repl
julia> using Polynomials, PolynomialRatios

julia> x = variable()
Polynomial(x)

julia> ex = 1 + x + x^2/2 + x^3/6 + x^4/24 + x^5/120 # e^xのテイラー多項式
Polynomial(1.0 + 1.0*x + 0.5*x^2 + 0.16666666666666666*x^3 + 0.041666666666666664*x^4 + 0.008333333333333333*x^5)

julia> maximum(abs, exp(x) - fit(RationalFunction, ex, 1,1)(x) for x ∈ 0:.05:0.5)
0.017945395966538547

julia> maximum(abs, exp(x) - fit(RationalFunction, ex, 1,2)(x) for x ∈ 0:.05:0.5)
0.0016624471707165078

julia> maximum(abs, exp(x) - fit(RationalFunction, ex, 2,1)(x) for x ∈ 0:.05:0.5)
0.001278729299871717

julia> maximum(abs, exp(x) - fit(RationalFunction, ex, 2,2)(x) for x ∈ 0:.05:0.5)
7.262205147950951e-5
```
