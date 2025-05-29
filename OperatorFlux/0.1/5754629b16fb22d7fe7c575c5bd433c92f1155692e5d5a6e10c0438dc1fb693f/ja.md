```
FourierTransform(; modes, even = true)
```

モード `modes` とスタイル `even` を持つ離散フーリエ変換を構築し、データの2次元目、3次元目、...N-modes+1次元目で動作します。

# 例

```
julia> FourierTransform(modes = (12, 3, 4, 12))
```
