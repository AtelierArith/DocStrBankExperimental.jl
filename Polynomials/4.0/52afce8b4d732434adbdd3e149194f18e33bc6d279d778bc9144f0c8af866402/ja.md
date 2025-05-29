```
AbstractUnivariatePolynomial{B,T,X} <: AbstractPolynomial{T,X}
AbstractDenseUnivariatePolynomial{B,T,X} <: AbstractUnivariatePolynomial{B,T,X}
AbstractLaurentUnivariatePolynomial{B,T,X} <: AbstractUnivariatePolynomial{B,T,X}
```

明示的な基底 `B` を持つ多項式のための抽象コンテナ型です。`AbstractDenseUnivariatePolynomial` は `0` ベースの多項式用であり、`AbstractLaurentUnivariatePolynomial` は不確定数の負の冪を持つ可能性のある多項式用です。
