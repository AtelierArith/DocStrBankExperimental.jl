```
grdmask(cmd0::String="", arg1=nothing, kwargs...)
```

1. 閉じたポリゴンを定義する1つ以上のパスファイルを読み込みます。
2. パスファイルは単にデータポイントの位置を表し、マスクはノードが最も近いデータポイントからの最大距離内にあるかどうかに応じて、内側または外側の値に設定されます。

## パラメータ

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [およびオプションで *y_inc*] はグリッドの間隔です。オプションで、増分単位を追加できます。
  * **A** | **steps** :: [Type => Str | Number]		$Arg = m|p|x|y$

    入力データが地理的である場合、ポリゴンの辺は大円弧によって近似されます。このオプションを使用すると、辺は直線と見なされます。
  * **C** | **clobber** :: [Type => Str]		$Arg = f|l|o|u$

    クラッシャーモード：z値によってグリッドノードを決定するポリゴンを選択します。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = grdmask(....) 形式を使用してください。
  * **N** | **out*edge*in** :: [Type => Str | List]    $Arg = [z|Z|p|P]values$

    ポリゴンの外側、エッジ上、または内側にあるノードに割り当てられるout/edge/inを設定します。値は任意の数値、テキスト文字列NaNを含むことができます [デフォルトは0/0/1]。
  * **S** | **search_radius** :: [Type => Str | List]    $Arg = search_radius[unit] |xlim/ylim$

    最寄りのデータポイントまでの距離に応じて、ノードを内側、エッジ上、または外側に設定します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告をstderrに送信する冗長性レベルを選択します。
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    プライマリ入力のネイティブバイナリ形式を選択します（セカンダリ入力は常にASCIIです）。
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    すべての入力列を調べ、任意の項目がnodataに等しい場合、この値を欠損データ項目として解釈し、値NaNに置き換えます。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含むASCIIデータレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します（時間または地理データ）。
  * **g** | **gap** :: [Type => Str]           $Arg = [a]x|y|d|X|Y|D|[col]z[+|-]gap[u]$

    連続するデータポイント間の間隔を調べ、ラインにブレークを課します。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    プライマリ入力の特定のデータ列を任意の順序で選択します。
  * **j** | **spherical_dist** | **spherical** :: [Type => Str]     $Arg = e|f|g$

    この機能をサポートするモジュールで球面距離がどのように計算されるかを決定します。
  * **n** | **interp** | **interpolation** :: [Type => Str]         $Arg = [b|c|l|n][+a][+bBC][+c][+tthreshold]$

    Bスプラインスムージングのためにbを追加することでグリッド補間モードを選択します。cはバイキュービック補間、lはバイリニア補間、nは最近傍値を示します。
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    ピクセルノードの登録を強制します [デフォルトはグリッドライン登録]。
  * **x** | **cores** | **n_threads** :: [Type => Str or Number]  $Arg = [[-]n]$

    OpenMP対応のマルチスレッドアルゴリズムで使用されるコアの数を制限します。(http://docs.generic-mapping-tools.org/latest/gmt.html#x-full)
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    入力レコードを循環座標に変換します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

完全なドキュメントを見るには、次のように入力してください: $@? grdmask$
