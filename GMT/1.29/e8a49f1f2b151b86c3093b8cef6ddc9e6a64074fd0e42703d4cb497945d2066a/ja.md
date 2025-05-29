```
Dtiles, zoomL = quadbounds(quadtree; geog=true, quadkey=['0' '1'; '2' '3'])
```

`quadtree`の座標を計算します。単一のquadtree文字列またはquadtree文字列の配列のいずれかです。

  * `quadtree`: 単一のquadtree文字列または`Matrix{String}`のquadtree文字列の配列です。これは、`mosaic`を呼び出して`quadonly`オプションを使用することで取得されるquadtree文字列または文字列の配列です（以下の例を参照）。
  * `quadkey=['0' '1'; '2' '3']`: quadtreeのquadkeyです。

### 戻り値

  * `Dtiles`: 各タイルのコーナー座標を持つGMTdatasetベクトル。
  * `zoomL`: タイルのズームレベル。

### 例

```jldoctest
  quadtree = mosaic([-10. -8],[37. 39.], zoom=8, quadonly=1)[1];
  D = quadbounds(quadtree)[1];
  viz(D)
```
