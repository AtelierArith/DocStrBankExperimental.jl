```
a ↠ b = flatmap(_ -> b, a) # \twoheadrightarrow
```

モナドのための便利な演算子で、最初のモナド内で2番目のモナドを適用するだけです。

演算子 ↠ (\twoheadrightarrow) は、他の好ましい演算子 ≫ (\gg) が [haskell unicode syntax for monads](https://hackage.haskell.org/package/base-unicode-symbols-0.2.4.2/docs/Control-Monad-Unicode.html) に従っているはずですが、残念ながら追加の意味を持つブール比較として解析されるため、非ブールの適用でエラーが発生します。

↠ は、この制限がなく、右結合である最も似ている他の演算子です。
