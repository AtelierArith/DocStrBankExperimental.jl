```
viz(object; kwargs...)
```

この関数は、プロット用の `UlamMethod` オブジェクトのために `Meshes.viz` をラップします。

### メソッド

```
viz(boundary; kwargs...)
```

境界をプロットします。

```
viz(bins; kwargs...)
```

ビンをプロットします。

```
viz(binner; kwargs...)
```

`binner.bins` をプロットします。

```
viz(data; kwargs...)
```

ポイントの `2 x N` 行列をプロットします。

```
viz(traj; kwargs...)
```

同じグラフに `traj.x0` と `traj.xT` をプロットします。

```
viz(ulam; bins_labels = true, bins_labels_size = 16)
```

ビン、境界、および `P_closed(ulam)` の定常分布のヒートマップをプロットします。

オプションで、`bin_labels` でビンラベルを重ね合わせ、`bins_labels_size` でそのサイズを調整します。

```
viz(traj, ulam; bins_labels = true, bins_labels_size = 16)
```

`traj.x0` と `traj.xT` の両方の各ビンのカウントのヒートマップをプロットします。

オプションで、`bin_labels` でビンラベルを重ね合わせ、`bins_labels_size` でそのサイズを調整します。

---

### `Meshes.viz` のドキュメント文字列は以下に示されています。

---

```
viz(object; [options])
```

さまざまな `options` を使用して Meshes.jl `object` を視覚化します。

## 利用可能なオプション

  * `color`        - 幾何学の色
  * `alpha`        - [0,1] の透明度
  * `colormap`     - ColorSchemes.jl からのカラースキーム/マップ
  * `colorrange`   - 最小および最大の色の値
  * `showsegments` - セグメントを視覚化
  * `segmentcolor` - セグメントの色
  * `segmentsize`  - セグメントの幅
  * `showpoints`   - ポイントを視覚化
  * `pointmarker`  - ポイントのマーカー
  * `pointcolor`   - ポイントの色
  * `pointsize`    - ポイントのサイズ

オプション `color` は、単一のスカラーまたはスカラーのベクトルであることができます。 [`Mesh`](@ref) サブタイプの場合、色のベクトルの長さは、色が頂点に割り当てられるべきか、要素に割り当てられるべきかを決定します。

## 例

異なる着色方法（頂点対要素）：

```
# 頂点着色（すなわち線形補間）
viz(mesh, color = 1:nvertices(mesh))

# 要素着色（すなわち離散色）
viz(mesh, color = 1:nelements(mesh))
```

幾何学の境界を表示するための異なる戦略（showsegments 対 boundary）：

```
# showsegments で境界を視覚化
viz(polygon, showsegments = true)

# 別の呼び出しで境界を視覚化
viz(polygon)
viz!(boundary(polygon))
```

### 注意事項

  * この関数は、Julia v1.9 以降の言語のパッケージ拡張を介して Makie.jl バックエンドが存在する場合にのみ機能します。
