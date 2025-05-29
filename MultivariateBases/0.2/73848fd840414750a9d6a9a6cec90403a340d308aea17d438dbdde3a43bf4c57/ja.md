```
struct MonomialBasis{MT<:MP.AbstractMonomial, MV<:AbstractVector{MT}} <: AbstractPolynomialBasis
    monomials::MV
end
```

ベクトル `monomials` のモノミアルを持つモノミアル基底。例えば、`MonomialBasis([1, x, y, x^2, x*y, y^2])` は変数 `x`、`y` における二次多項式の部分空間のためのモノミアル基底です。

この基底は、密度として複素ガウス測度を用いて定義されたスカラー積の下で直交しています。このスカラー積に対して正規直交になるように正規化されると、[`ScaledMonomialBasis`](@ref) が得られます。
