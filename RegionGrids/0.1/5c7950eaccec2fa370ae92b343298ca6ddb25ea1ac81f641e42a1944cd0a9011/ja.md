```
UnstructuredGrid
```

`UnstructuredGrid`は、キューブスフィアや非構造メッシュグリッドでよく使用される非構造グリッドに基づいて作成された`RegionGrid`です。

すべての`UnstructuredGrid`タイプは、以下のフィールドを含みます：

  * `lon` - 領域を説明するRegionGrid内の各点の経度を定義する`Float`のベクター。
  * `lat` - 領域を説明するRegionGrid内の各点の緯度を定義する`Float`のベクター。
  * `ipoint` - 元の非構造グリッドからRegionGridに抽出された有効な点のインデックスを定義する`Int`のベクター。
