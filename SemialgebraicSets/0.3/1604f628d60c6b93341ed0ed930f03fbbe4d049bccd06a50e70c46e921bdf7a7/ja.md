```
standard_monomials(I::AbstractPolynomialIdeal, vars = variables(I))
```

理想 `I` の変数 `var` における *標準モノミアル* のベクトルを返します。モノミアルは、理想の任意の多項式の先頭モノミアルでない場合に *標準モノミアル* です。そのようなモノミアルが無限に存在する場合、`nothing` が返されます。

詳細については、[CLO5, p. 38] を参照してください。ここでは *基底モノミアル* とも呼ばれています。

[CLO05] Cox, A. David & Little, John & O'Shea, Donal *Using Algebraic Geometry*. Graduate Texts in Mathematics, **2005**. https://doi.org/10.1007/b138611
