```
filter(f, signal)
```

`f` が `false` を返す場合、`signal` から更新を削除します。フィルターは、`f(value(signal))` が true を返すまで、信号の現在の値を保持します。
