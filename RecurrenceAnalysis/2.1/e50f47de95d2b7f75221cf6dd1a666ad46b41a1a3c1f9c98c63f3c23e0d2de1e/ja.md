```
recurrence_threshold(rt::AbstractRecurrenceType, x [, y] [, metric]) → ε
```

`rt`のために計算された距離の閾値`ε`を返します。出力は実数ですが、`rt`が`LocalRecurrenceRate`のインスタンスである場合、`ε`は`Vector`になります。
