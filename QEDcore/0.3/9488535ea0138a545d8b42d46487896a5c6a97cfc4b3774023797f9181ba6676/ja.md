```
coordinate_name(coord::AbstractUnivariateCoordinate)
```

単一の一変数座標の名前を取得します。

# 引数

  * `coord::AbstractUnivariateCoordinate`: 一つの一変数座標で、自由度が1の座標系を表す `AbstractCoordinateSet{1}` のサブタイプです。

# 戻り値

  * 座標の名前を表す文字列。

この関数は単一の座標に対する人間が読みやすいラベルを提供し、一般的に散乱過程や位相空間における個々の座標に名前を付けるために使用されます。
