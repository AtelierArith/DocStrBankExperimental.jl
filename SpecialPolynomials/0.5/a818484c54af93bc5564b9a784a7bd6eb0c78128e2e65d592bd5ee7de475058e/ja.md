```
Bernstein{N, T, X}
```

[バーンスタイン多項式](https://en.wikipedia.org/wiki/Bernstein_polynomial)は、バーンスタイン基本多項式を用いて表現された多項式です。各次数 `𝐍` に対して、これは次の形の `𝐍` 次多項式のセットであり、`𝐍+1` 個の多項式から構成されます: `β_{𝐍,ν} =  (ν choose 𝐍) x^ν  (1-x)^{𝐍-ν}`、`0 ≤ x ≤ 1.`

`Bernstein{𝐍,T}` 型は、次数 `𝐍` 以下の多項式を表し、基底ベクトルの線形結合を型 `T` の係数を用いて表現します。

```jldoctest Bernstein
julia> using Polynomials, SpecialPolynomials

julia> p = basis(Bernstein{3},  2)
Bernstein(1⋅β₃,₂(x))

julia> convert(Polynomial, p)
Polynomial(3.0*x^2 - 3.0*x^3)
```

!!! note
    [StaticUnivariatePolynomials](https://github.com/tkoolen/StaticUnivariatePolynomials.jl) は、より高性能なバージョンを提供します。

