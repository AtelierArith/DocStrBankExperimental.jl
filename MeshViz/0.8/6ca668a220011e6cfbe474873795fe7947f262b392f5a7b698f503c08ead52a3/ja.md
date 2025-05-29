```
viz(object)
```

Meshes.jl `object`をさまざまなオプションで視覚化します：

  * `color`       - 幾何学またはポイントの色
  * `alpha`       - [0,1]の範囲の透明度チャネル
  * `colorscheme` - ColorSchemes.jlからのカラースキーム
  * `facetcolor`  - ファセットの色（例：エッジ）
  * `showfacets`  - ファセットを表示するかどうかを示します
  * `pointsize`   - ポイントセット内のポイントのサイズ
  * `segmentsize` - セグメントのサイズ（または幅）

オプション`color`は、単一のスカラーまたはスカラーのベクトルであることができます。メッシュの場合、色のベクトルの長さは、色が頂点または要素に割り当てられるべきかどうかを決定します。

## 例

```
# 頂点の色付け（すなわち線形補間）
viz(mesh, color = 1:nvertices(mesh))

# 要素の色付け（すなわち離散的な色）
viz(mesh, color = 1:nelements(mesh))
```
