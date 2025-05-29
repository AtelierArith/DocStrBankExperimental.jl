```
struct OrthonormalCoefficientsBasis{PT<:MP.AbstractPolynomialLike, PV<:AbstractVector{PT}} <: AbstractPolynomialBasis
    polynomials::PV
end
```

ベクトル `polynomials` の多項式を持つ多項式基底で、係数の内積から導出された内積に関して直交正規です。例えば、`FixedPolynomialBasis([1, x, 2x^2-1, 4x^3-3x])` は変数 `x` における三次多項式のためのチェビシェフ多項式基底です。
