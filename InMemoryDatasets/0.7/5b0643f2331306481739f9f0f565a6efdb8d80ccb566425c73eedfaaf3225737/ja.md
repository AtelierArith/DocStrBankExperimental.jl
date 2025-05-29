```
setformat!(ds::Dataset, col, f)
setformat!(ds::Dataset, col => f)
setformat!(ds::Dataset, col1 => f1, col2 => f2, ...)
setformat!(ds::Dataset, cols => f)
```

指定された `columns` のフォーマットを `ds` に設定します。
