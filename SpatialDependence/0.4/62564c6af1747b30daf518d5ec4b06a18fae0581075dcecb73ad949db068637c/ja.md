```
wtransform!(W::SpatialWeights, style::Symbol)
```

指定された$style$を使用して重みをインプレースで変換します。

# 重みの変換

`style`は次のいずれかであることができます：

  * `:binary`: 隣接していれば1、そうでなければ0。
  * `:row`: 行標準化。各行の合計は1になります。
