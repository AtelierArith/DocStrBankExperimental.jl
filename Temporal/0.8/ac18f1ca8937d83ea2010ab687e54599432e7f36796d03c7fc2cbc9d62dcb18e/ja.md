```
eow(x::TS; cal::Bool=false)
```

入力の週の終わりに発生するすべての観測値を含む時系列を返します。

  * `cal`が`false`の場合、週の最後のカレンダー日で発生する観測値のみが返されます
  * `cal`が`true`の場合、次のインデックスが新しい週であるすべての観測値が返されます
