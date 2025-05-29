```
term(coef, mono::AbstractMonomialLike)
```

係数 `coef` と単項式 `mono` を持つ項を返します。これと `coef * mono` の間には2つの重要な違いがあります：

  * `term(coef, mono)` は `coef` と `mono` をコピーしないため、この項を MutableArithmetics で修正すると、この関数の入力が変更される可能性があります。これを避けるためには、`term(MA.copy_if_mutable(coef), MA.copy_if_mutable(mono))` を呼び出してください。ここで `MA = MutableArithmetics` です。
  * 例えば `coef = (x + 1)` で `mono = x^2` の場合、`coef * mono` は整数係数の多項式 `x^3 + x^2` を返しますが、`term(x + 1, x^2)` は多項式係数 `x + 1` を持つ項を返します。

    term(p::AbstractPolynomialLike)

多項式 `p` を項に変換します。多項式に適用すると、項が1つ以上ある場合は `InexactError` をスローします。項に適用すると、それは恒等であり、コピーは行いません。単項式に適用すると、`AbstractTerm{Int}` 型の項を作成します。
