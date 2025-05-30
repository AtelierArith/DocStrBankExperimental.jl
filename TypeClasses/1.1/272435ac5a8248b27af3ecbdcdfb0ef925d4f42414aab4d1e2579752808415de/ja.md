```
a ↠ b = flatmap(_ -> b, a) # \twoheadrightarrow
```

モナドのための便利な演算子で、最初のモナド内で2番目のモナドを適用するだけです。

演算子 ↠ (\twoheadrightarrow) は、他の好ましい演算子 ≫ (\gg) が [haskell unicode syntax for monads](https://hackage.haskell.org/package/base-unicode-symbols-0.2.4.2/docs/Control-Monad-Unicode.html) に従っているはずですが、残念ながらブール比較として解析され、非ブールアプリケーションでエラーを引き起こす追加の意味を持つため、選ばれました。

↠ は、この制限がなく、右結合である他の最も似た見た目の演算子です。
