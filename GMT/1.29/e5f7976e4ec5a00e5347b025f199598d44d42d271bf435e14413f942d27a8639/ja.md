```
sphdistance(cmd0::String="", arg1=nothing, kwargs...)
```

球面上にVoronoi距離、ノード、または自然最近傍グリッドを作成します

完全なGMT（`GMT.jl`ではない）ドキュメントは[`sphdistance`](http://docs.generic-mapping-tools.org/latest/sphdistance.html)を参照してください。

## パラメータ

  * **C** | **save_mem** :: [Type => Bool]

    大規模データセットの場合、メモリを節約できます（処理が増える代償として）。
  * **D** | **duplicates** :: [Type => Bool]

    重複するポイントを削除します [デフォルトでは重複がないと仮定します]。
  * **E** | **quantity** :: [Type => Str]   $Arg = d|n|z[dist]$

    グリッドノードに割り当てるべき量を指定します。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = sphdistance(....)の形式を使用してください。
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [およびオプションで*y_inc*]はグリッド間隔です。オプションで、増分単位を追加します。
  * **L** | **dist_unit** :: [Type => Str]      $Arg = d|e|f|k|M|n|u$

    距離計算に使用される単位を指定します。
  * **N** | **nodes** :: [Type => Str]      $Arg = nodes$

    各Voronoiポリゴンに関連する情報（ユニークなノードの経度、緯度、およびポリゴン面積）を別のファイルから読み込みます。
  * **Q** | **voronoi** :: [Type => Str]     $Arg = voronoifile$

    事前に計算されたVoronoiポリゴンを含むファイルの名前を追加します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告をstderrに送信する冗長性レベルを選択します。
  * **b** | **binary** :: [Type => Str]
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    ユーザーがコーディングした欠損データ値がGMTの公式NaN値にどのように変換されるかを制御します。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含むASCIIデータレコードのみを受け入れます。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    主な入力ファイルにはヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    主な入力の特定のデータ列を任意の順序で選択します。
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    ピクセルノードの登録を強制します [デフォルトはグリッドライン登録]。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

完全なドキュメントを見るには、次のように入力してください: $@? sphdistance$
