```
nvariables(p::AbstractPolynomialLike)
```

`p`の変数の数を返します。すなわち、`length(variables(p))`です。これは、非ゼロ次数の変数の数よりも多い場合があります（[`variables`](@ref)の例のセクションを参照してください）。

### 例

`nvariables(x^2*y)`を呼び出すと、少なくとも2が返され、`nvariables(x)`を呼び出すと、少なくとも1が返されるべきです。
