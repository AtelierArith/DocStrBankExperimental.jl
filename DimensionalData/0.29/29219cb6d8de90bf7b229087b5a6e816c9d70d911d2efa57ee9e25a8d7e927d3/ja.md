```
val(x)
val(dims::Tuple) => Tuple
```

ラッパーオブジェクトの含まれている値を返します。

`dims` は `Dimension`、`Dimension` タイプ、または `Dim{Symbol}` のための `Symbols` であることができます。

`val` メソッドを定義していないオブジェクトは変更されずに返されます。
