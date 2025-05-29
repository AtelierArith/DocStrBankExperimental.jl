```
maprange(f, start; stop, length)
maprange(f; start, stop, length)
maprange(f, start, stop; length)
```

`length` の値は `start` と `stop` の間にあり、`f(x)` は均等なステップで増加します。配列を具現化しないように `mapview` を使用します。

`maprange(identity, ...)` は `range(...)` と同等です。最も一般的な用途は対数間隔の範囲です：

`maprange(log, 10, 1000, length=5) ≈ [10, 31.6227766, 100, 316.227766, 1000]`

他の変換も有用です：

`maprange(sqrt, 16, 1024, length=5) == [16, 121, 324, 625, 1024]`
