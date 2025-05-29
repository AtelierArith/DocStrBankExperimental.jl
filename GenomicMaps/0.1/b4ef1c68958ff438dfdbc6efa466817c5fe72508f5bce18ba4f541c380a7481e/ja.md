```
function drawplasmid(chr; kwargs...)
```

円形プラスミドマップを描画します。CDSは、+ストランドおよび-ストランドの遺伝子に対して、それぞれプラスミドの外側と内側にボックスとして表示されます。サポートされているkwargsは次のとおりです：

  * outfile           出力ファイルへのパス。サポートされているファイルタイプはPNG、SVG、PDF、およびEPSです。
  * drawingsize       図のサイズ。`Tuple{Int,Int}`または「1000x1000」のような`String`で指定できます。
  * title             プラスミドの名前。
  * ORI               ORIの位置（デフォルトは1）。
  * colors            `Gene`をキー、色を値とする`Dict`（デフォルトは`defaultgenecolor`）。
  * defaultgenecolor  デフォルトは:lightgrey。
  * annotations       各CDSの注釈を含む`Vector`。
  * internalcolors    ヌクレオチド位置を表す`UnitRange`をキー、色を値とする`Dict`。遺伝子の一部や遺伝子間領域の色付けに使用できます。
  * genethickness     遺伝子ボックスのサイズ。
  * textoffset        注釈が描画されるプラスミドからの距離。
  * figureoffset      x軸とy軸のオフセットを持つ`Tuple{Int,Int}`。片側に注釈が多い場合に便利です。
  * genegroups        遺伝子番号を表す`UnitRanges`をキー、`NamedTuples`を値とする`Dict`。タプルには`text`フィールドが必要で、グループの注釈を含み、さらに`placement`（:outerまたは:inner）、`offset`、`textoffset`、および`thickness`を取ることができます。
