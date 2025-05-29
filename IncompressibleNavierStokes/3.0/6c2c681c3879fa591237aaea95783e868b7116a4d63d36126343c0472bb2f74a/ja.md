圧力点における `state` フィールドをプロットします。`state` が `Observable` の場合、プロットはインタラクティブになります。

利用可能なフィールド名は次のとおりです：

  * `:velocity`,
  * `:vorticity`,
  * `:streamfunction`,
  * `:pressure`。

2D の利用可能なプロット `type` は次のとおりです：

  * `heatmap` (デフォルト),
  * `image`,
  * `contour`,
  * `contourf`。

3D の利用可能なプロット `type` は次のとおりです：

  * `contour` (デフォルト)。

`alpha` 値は 3D の `contour` に渡されます。
