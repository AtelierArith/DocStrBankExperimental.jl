```
localanisotropies(Geometric, searcher; simplify=true)
```

検索オブジェクトから `LocalAnisotropy` を抽出します。空間データと検索オブジェクトからのパラメータに基づいて、各地点で隣接点のグループが収集されます。PCAがその空間座標に適用され、よりクラスター化された点の方向に整列した局所的な楕円/楕円体を表す固有ベクトルが返されます。大きさはPCAの固有値の比率です。3-D表面点から局所的な異方性を抽出するのに役立ちます。`simplify = true` でデータが3-Dの場合、PCAから最小方向のみが抽出され、他の軸は計算されます（主方向は常に最大傾斜方向に沿い、中間軸は他の軸に直交します）。これは3-Dのデフォルトです。

## 例

```julia
searcher = KNearestSearch(pts3dsurface, 10)
prelpars = localanisotropies(Geometric, searcher) # 表面での局所的なパラメータを抽出
lpars = idwpars(prelpars, searcher, grid) # 局所的なパラメータをグリッドに補間
```
