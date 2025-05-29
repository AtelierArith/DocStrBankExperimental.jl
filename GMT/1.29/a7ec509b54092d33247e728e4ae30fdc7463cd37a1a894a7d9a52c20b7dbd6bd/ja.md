```
nearneighbor(cmd0::String="", arg1=nothing; kwargs...)
```

任意の位置にある (x,y,z[,w]) トリプル [四重項] を読み取り、最近傍アルゴリズムを使用して、ノードの中心にある半径内に1つ以上のポイントがある各ノードに平均値を割り当てます。平均値は、検索半径内の各セクターからの最近傍ポイントの加重平均として計算されます。使用される重み関数は w(r) = 1 / (1 + d ^ 2) であり、ここで d = 3 * r / search_radius で、r はノードからの距離です。この重みは、観測ポイントの重み [提供されている場合] によって調整されます。

## パラメータ

  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [およびオプションで *y_inc*] はグリッド間隔です。オプションで、インクリメント単位を追加します。
  * **N** | **sectors** | **nn** | **nearest** :: [Type => Number | Str | Bool (for nn or nearest)]

    各ノードの中心にある円形領域は `sectors` セクターに分割されます。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定します。
  * **S** | **search_radius** :: [Type => Number]

    ノードに近いと見なされるデータポイントを決定する検索半径を設定します。
  * **E** | **empty** :: [Type => Bool]

    G が設定されているときに空のノードに割り当てられる値を設定します [NaN]。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = nearneighbor(....) 形式を使用してください。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告を stderr に送信する冗長性レベルを選択します。
  * **W** | **weights** :: [Type => Bool]

    入力データには観測ポイントの重みを含む4番目の列があります。
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    主入力のネイティブバイナリ形式を選択します（副入力は常に ASCII です）。
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    すべての入力列を調べ、任意の項目が nodata と等しい場合、この値を欠損データ項目として解釈し、値 NaN に置き換えます。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含む ASCII データレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します（時間または地理データ）。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    主入力ファイルにヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    主入力の特定のデータ列を任意の順序で選択します。
  * **n** | **interp** | **interpolation** :: [Type => Str]         $Arg = [b|c|l|n][+a][+bBC][+c][+tthreshold]$

    Bスプラインスムージングのために b を追加するか、バイキュービック補間のために c を追加するか、バイリニア補間のために l を追加するか、最近傍値のために n を追加してグリッド補間モードを選択します。
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    ピクセルノードの登録を強制します [デフォルトはグリッドライン登録]。
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    入力レコードを循環座標に変換します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

完全なドキュメントを見るには、次のように入力してください: $@? nearneighbor$ ```
