```
struct FixedPolynomialBasis{PT<:MP.AbstractPolynomialLike, PV<:AbstractVector{PT}} <: AbstractPolynomialBasis
    polynomials::PV
end
```

ベクトル `polynomials` の多項式を持つ多項式基底。例えば、`FixedPolynomialBasis([1, x, 2x^2-1, 4x^3-3x])` は変数 `x` における三次多項式のチェビシェフ多項式基底です。
