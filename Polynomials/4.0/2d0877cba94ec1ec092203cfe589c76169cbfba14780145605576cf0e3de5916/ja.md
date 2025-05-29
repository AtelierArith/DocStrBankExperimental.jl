```
coeffs(::AbstractPolynomial)
coeffs(::AbstractDenseUnivariatePolynomial)
coeffs(::AbstractLaurentUnivariatePolynomial)
```

密な単変数多項式の場合、係数 $(a_0, a_1, \dots, a_n)$ を反復可能な形で返します。これはベクトルまたはタプルであり、多項式の係数をエイリアスすることがあります。

ローレンツ型多項式（例：`LaurentPolynomial`、`SparsePolynomial`）の場合、係数 $(a_i, a_{i+1}, \dots, a_j)$ を返します。ここで、$i$ は `firstindex(p)` から、$j$ は `lastindex(p)` から見つかります。

`LaurentPolynomial` と `SparsePolynomial` に対しては、`pairs` イテレータがより一般的に便利であり、$p_i = 0$ の項をスキップしながら $(i, p_i)$ を反復します。

デフォルトは `p.coeffs` です。
