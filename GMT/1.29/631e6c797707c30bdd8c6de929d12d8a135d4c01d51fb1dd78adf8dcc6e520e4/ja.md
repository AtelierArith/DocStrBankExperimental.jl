```
gmtspatial(cmd0::String="", arg1=nothing, kwargs...)
```

ポイント、ライン、ポリゴンに関する地理空間操作。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`gmtspatial`](http://docs.generic-mapping-tools.org/latest/gmtspatial.html)を参照してください。

## パラメータ

  * **A** | **nn** | **nearest_neighbor** :: [Type => Str]     `Arg = [amin_dist][unit]`

    空間最近隣（NN）分析を実行します：各ポイントの最近隣を特定し、NN距離と各ペアに関与するポイントIDを報告します。
  * **C** | **clip** :: [Type => Bool]

    ポリゴンを地図領域にクリップし、必要に応じて地図の境界をポリゴンに含めます。結果は閉じたポリゴンになります。
  * **D** | **duplicates** :: [Type => Str]   `Arg = [+ffile][+aamax][+ddmax][+c|Ccmax][+sfact]`

    入力ラインまたはポリゴンの間で重複をチェックします。ファイルが+fで指定されている場合、入力フィーチャがファイル内のフィーチャに既に存在するかどうかをチェックします。
  * **E** | **handedness** :: [Type => Str]  `Arg = +|-`

    すべてのポリゴンの手の向きを、指定された+（反時計回り）または-（時計回り）に合わせてリセットします。Q+を含意します。
  * **F** | **force_polygons** :: [Type => Str | []]   `Arg = [l]`

    入力データを出力時にポリゴンに強制的に変換します。すなわち、すでに閉じていない場合は明示的に閉じます。オプションで、lを追加してラインジオメトリを強制します。
  * **I** | **intersections** :: [Type => Str | []]   `Arg = [e|i]`

    すべてのポリゴンのペア間の交差点の位置を特定します。
  * **N** | **in_polygons** | **in_polyg** :: [Type => Str]     `Arg = pfile[+a][+pstart][+r][+z]`

    入力データ内の各フィーチャの1つ（またはすべて、+aを使用）ポイントが、pfileで指定されたポリゴンのいずれかの内部にあるかどうかを判断します。
  * **Q** | **centroid** or **area** or **length** :: [Type => Str]      `Arg = [[unit][+cmin[/max]][+h][+l][+p][+s[a|d]]`

    すべてのポリゴンの面積またはラインセグメントの長さを測定します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定します。
  * **S** | **polygons** :: [Type => Str]     `Arg = h|i|j|s|u`

    ポリゴンの空間処理。
  * **T** | **truncate** :: [Type => Str | []]     `Arg = [clippolygon]`

    指定されたポリゴンに対してポリゴンを切り詰め、オープンポリゴンになる可能性があります。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **W** | **extend** :: [Type => Str | Tuple]     `Arg = <dist>[<unit>][+f|l]`

    すべてのセグメントを、元の端点から<dist>単位離れた方向に追加の最初と最後のポイントで拡張します。

```
