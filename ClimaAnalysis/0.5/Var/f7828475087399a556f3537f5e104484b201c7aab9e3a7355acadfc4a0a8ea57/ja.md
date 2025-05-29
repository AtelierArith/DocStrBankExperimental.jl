```
variance_lon(var; ignore_nan = true)
```

新しいOutputVarを返し、値は経度次元に沿った分散です。

`corrected`が`true`の場合、分散はサンプル平均を`n - 1`で割ることによって計算されます。一方、`corrected`が`false`の場合、分散はサンプル平均を`n`で割ることによって計算されます。ここで、`n`は分散が計算される要素の数です。
