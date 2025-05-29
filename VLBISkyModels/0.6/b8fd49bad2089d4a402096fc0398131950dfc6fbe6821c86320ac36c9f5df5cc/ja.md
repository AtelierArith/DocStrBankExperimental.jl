```
modify(img::IntensityMap, transforms...)
```

これは `transforms...` を適用することによって `img` を変更し、変換された `IntensityMap` を返します。

!!! note



`modify` が `<:AbstractModel` に適用される場合とは異なり、これはすでに変更された画像を返します。
