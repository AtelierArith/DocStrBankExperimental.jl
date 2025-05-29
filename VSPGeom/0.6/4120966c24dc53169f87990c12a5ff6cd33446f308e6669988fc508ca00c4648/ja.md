```
degenGeomSize(degenGeom::DataFrame)
```

退化幾何を記述する2次元メッシュデータ構造のサイズを取得します。これは、DataFrame内の変数の数と合計ポイント数を取得するために使用される`size(degenGeom)`とは異なります。

**引数**

  * `degenGeom::DataFrame`: [`VSPComponent`](@ref)オブジェクト内のdegenGeomの1つ

**戻り値**

  * `nx::Int`: 通常、OpenVSPでXsecsと呼ばれる断面の数を表します
  * `ny::Int`: 通常、OpenVSPの各断面内のポイントの数を表します
