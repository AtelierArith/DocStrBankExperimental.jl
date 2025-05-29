```
filter(f, default, signal)
```

`signal` から `f` が `false` を返す更新を削除します。フィルターは、f(value(signal)) が true を返すまで default の値を保持し、その時に value(signal) に更新されます。
