```
variance_lat(var; ignore_nan = true, corrected = true)
```

緯度次元に沿った分散の値を持つ新しいOutputVarを返します。

`corrected`が`true`の場合、分散はサンプル平均を`n - 1`で割ることによって計算されます。一方、`corrected`が`false`の場合、分散はサンプル平均を`n`で割ることによって計算されます。ここで、`n`は分散が計算される要素の数です。
