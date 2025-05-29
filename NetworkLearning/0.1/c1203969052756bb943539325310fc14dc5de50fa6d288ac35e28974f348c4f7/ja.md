```
intdim(::LearnBase.ObsDimension)
```

次元オブジェクトに関連付けられた整数を返します。つまり、`intdim(ObsDim.Constant{3})` は `3` を返します。この関数は行列で動作するように設計されているため、`intdim(::ObsDim.Last)` は `2` を返します。
