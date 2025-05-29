```
requires_exactly1(method::AbstractReformulationMethod)
```

`method`が各選言に対して`Exactly 1`の選択肢が真である必要があるかどうかを示す`Bool`を返します。新しい再定式化メソッドタイプの場合、この制約が必要な場合は`true`を返すように拡張する必要があります（デフォルトでは`false`）。
