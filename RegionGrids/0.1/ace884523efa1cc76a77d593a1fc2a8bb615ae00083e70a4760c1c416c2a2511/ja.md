```
RectilinearGrid <: RegionGrid
```

`RectilinearGrid`は、直交経度/緯度グリッドに基づいて作成された`RegionGrid`です。独自のサブタイプを持っています：`RectGrid`、`TiltGrid`、および`PolyGrid`。

すべての`RectilinearGrid`タイプには、以下のフィールドが含まれています：

  * `lon` - 領域を説明する経度ベクトルを定義する`Float`のベクター。
  * `lat` - 領域を説明する緯度ベクトルを定義する`Float`のベクター。
  * `ilon` - 入力経度ベクトルから経度ベクトルを抽出するために使用されるインデックスを定義する`Int`のベクター。
  * `ilat` - 入力緯度ベクトルから緯度ベクトルを抽出するために使用されるインデックスを定義する`Int`のベクター。
  * `mask` - データが有効なRegionGrid内のグリッドポイントを定義するNaNと1の配列。
