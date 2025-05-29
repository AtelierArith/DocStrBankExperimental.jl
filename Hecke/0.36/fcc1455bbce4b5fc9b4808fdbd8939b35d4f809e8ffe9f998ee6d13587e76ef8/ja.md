```
idempotents(x::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, y::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> AbsSimpleNumFieldOrderElem, AbsSimpleNumFieldOrderElem
```

要素 `e in x`、`f in y` からなるタプル `(e, f)` を返します。ここで `1 = e + f` です。

イデアルが互いに素でない場合、エラーが発生します。
