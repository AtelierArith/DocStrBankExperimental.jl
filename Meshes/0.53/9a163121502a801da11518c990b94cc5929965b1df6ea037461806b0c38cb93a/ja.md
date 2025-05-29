```
viz(object; [options])
```

さまざまな `options` を使用して、Meshes.jl `object` を視覚化します。

## 利用可能なオプション

  * `color`        - 幾何学の色
  * `alpha`        - 透明度 [0,1] の範囲
  * `colormap`     - ColorSchemes.jl からのカラースキーム/マップ
  * `colorrange`   - 最小および最大の色の値
  * `showsegments` - セグメントを視覚化
  * `segmentcolor` - セグメントの色
  * `segmentsize`  - セグメントの幅
  * `showpoints`   - ポイントを視覚化
  * `pointmarker`  - ポイントのマーカー
  * `pointcolor`   - ポイントの色
  * `pointsize`    - ポイントのサイズ

オプション `color` は、単一のスカラーまたはスカラーのベクトルであることができます。[`Mesh`](@ref) サブタイプの場合、色のベクトルの長さは、色が頂点に割り当てられるべきか、要素に割り当てられるべきかを決定します。

## 例

異なる着色方法（頂点 vs. 要素）：

```
# 頂点の着色（すなわち線形補間）
viz(mesh, color = 1:nvertices(mesh))

# 要素の着色（すなわち離散的な色）
viz(mesh, color = 1:nelements(mesh))
```

幾何学の境界を表示するための異なる戦略（showsegments vs. boundary）：

```
# showsegments で境界を視覚化
viz(polygon, showsegments = true)

# 別の呼び出しで境界を視覚化
viz(polygon)
viz!(boundary(polygon))
```

### 注意

この関数は、Julia v1.9 以降の言語のパッケージ拡張を介して Makie.jl バックエンドが存在する場合にのみ機能します。
