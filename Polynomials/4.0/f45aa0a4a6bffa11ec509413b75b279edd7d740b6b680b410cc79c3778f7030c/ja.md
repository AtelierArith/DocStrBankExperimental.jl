```
RationalFunction(p::AbstractPolynomial, q::AbstractPolynomial)
p // q
```

2つの多項式から有理式（`p//q`）を作成します。

共通因子は、基本の`Rational`型のようにコンストラクタによってキャンセルされません。 [`lowest_terms`](@ref)関数がその操作を試みます。

反復の目的のために、有理関数は2要素のコンテナのように扱われます。

## 例

```julia-repl
julia> using Polynomials

julia> p,q = fromroots(Polynomial, [1,2,3]), fromroots(Polynomial, [2,3,4])
(Polynomial(-6 + 11*x - 6*x^2 + x^3), Polynomial(-24 + 26*x - 9*x^2 + x^3))

julia> pq = p // q
(-6 + 11*x - 6*x^2 + x^3) // (-24 + 26*x - 9*x^2 + x^3)

julia> lowest_terms(pq)
(-0.333333 + 0.333333*x) // (-1.33333 + 0.333333*x)

julia> pq(2.5)
-1.0

julia> pq(2) # uses first non-`0/0` ratio of `p⁽ᵏ⁾/q⁽ᵏ⁾`
-0.5

julia> pq^2
(36 - 132*x + 193*x^2 - 144*x^3 + 58*x^4 - 12*x^5 + x^6) // (576 - 1248*x + 1108*x^2 - 516*x^3 + 133*x^4 - 18*x^5 + x^6)

julia> derivative(pq)
(-108 + 180*x - 111*x^2 + 30*x^3 - 3*x^4) // (576 - 1248*x + 1108*x^2 - 516*x^3 + 133*x^4 - 18*x^5 + x^6)
```

!!! note
    [RationalFunctions.jl](https://github.com/aytekinar/RationalFunctions.jl)パッケージはアイデアの有用なソースでした。


!!! note
    `ImmutablePolynomial`型は有理関数には使用できません。この型は、分子と分母が正確に同じ型であることを要求します。

