```
treeplot(tree; kwargs...)
```

# 引数:

  * tree、`AbstractTrees.children()` が定義された木のルートノード。すべてのノードは `AbstractTrees.PreOrderDFS()` イテレータを使用して到達可能である必要があります。

# キーワード引数:

  * `showroot::Bool = false`、`BasicTreePlots.distance()` がルートに対して `nan` でない場合、ルートと親を結ぶ線を表示します。
  * `layoutstyle::Symbol = :dendrogram` 利用可能なオプションは `:dendrogram` または `:cladogram` です。

      * `:dendrogram` は、親ノードと子ノード間の距離を `BasicTreePlots.distance(node)` から計算して考慮した木を表示します。距離が定義されていない場合、デフォルトは `1` で、`：cladogram` レイアウトと同等です。
      * `:cladogram` は、各子ノードから親ノードへの距離が `1` に設定された木を表示します。
  * `branchstyle::Symbol = :square` 利用可能なオプションは `:square` または `:straight` です。

      * `:square` は、子から親への線を親の高さに戻ってから、直角で親ノードに接続するように表示します。
      * `straight` は、子から親への線を子から親への直線として表示します。
  * `linecolor = :black`、Makie の `lines` プロットの `color` オプションと一致する必要があります。単一の色 `:black`、色とアルファ透明度 `(:black, 0.5)`、または前ウォーク順の各ノードの数値ベクトルのいずれかにすることができます。各ノードの色は、それを親に接続する線に関連付けられています。
  * `linewidth = 1`、Makie の `lines` プロットの `linewidth` オプションと一致する必要があります。単一の幅または前ウォーク順の各ノードの数値ベクトルのいずれかにすることができます。各ノードの幅は、それを親に接続する線に関連付けられています。
  * `linecolormap=:viridis`  `linecolor` に関連付けられたカラーマップ。既知のカラーマップのシンボルまたは `cgrad()` から作成されたグラデーションである可能性があります。 [Makie の色のドキュメント](https://docs.makie.org/v0.21/explanations/colors) を参照してください。
  * `branch_point_resolution = 25`、各線分に関連付けられたポイントの数。プロット速度を上げるために減少させることができます。あるいは、滑らかであるべき線が滑らかでない場合は増加させることができます。
  * `usemaxdepth = false`、`true` の場合、各葉の先端からルートから最も遠い葉の深さまでのガイドラインを描画します。葉を y 軸（または `PolarAxis` にプロットされた場合は θ 軸）上の位置に接続するのに便利です。
  * `tipannotationsvisible::Bool = true`、各葉の先端にテキストラベルを表示するかどうか。
  * `tipfontsize = 9.0f0`、先端ラベルが表示されるフォントサイズ。
  * `openangle = 0`、`PolarAxis` にプロットされたときに円の周りの木のスパンを制限するラジアン単位の角度。`openangle = deg2rad(5)` の場合、葉の先端は角度 `0` から `(2π - openangle)` に広がります。
  * `tipalign = (:left, :center)` 先端ラベルのテキストの整列。 [Makie のオプション](https://docs.makie.org/v0.21/reference/plots/text#alignment) を参照してください。
  * `tipannotationoffset = (3.0f0, 0.0f0)` 実際の先端位置からの先端ラベルのオフセット。最初の値は `x` 軸に関連付けられ、2 番目の値は `y` 軸に関連付けられています。（現在、直交軸にのみ利用可能です）
