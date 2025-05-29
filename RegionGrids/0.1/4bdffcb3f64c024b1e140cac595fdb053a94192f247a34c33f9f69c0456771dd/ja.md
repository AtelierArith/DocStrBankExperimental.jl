```
GeneralizedGrid
```

`GeneralizedGrid`は、**直線的でない**経度/緯度グリッドに基づいて作成された`RegionGrid`です。これは、曲線的なグリッドから非構造的なグリッドまでさまざまです。独自のサブタイプを持っています：`RegionMask`と`VectorMask`。

すべての`GeneralizedGrid`タイプは、以下のフィールドを含みます：

  * `lon` - 領域を記述するRegionGrid内の各点の経度を定義する`Float`の行列。
  * `lat` - 領域を記述するRegionGrid内の各点の緯度を定義する`Float`の行列。
  * `ilon` - 入力経度ベクトルから経度ベクトルを抽出するために使用されるインデックスを定義する`Int`のベクトル。
  * `ilat` - 入力緯度ベクトルから緯度ベクトルを抽出するために使用されるインデックスを定義する`Int`のベクトル。
  * `mask` - データが有効なRegionGrid内のグリッドポイントを定義するNaNと1の配列。
