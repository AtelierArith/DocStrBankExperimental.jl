```
grdcontour(cmd0::String="", arg1=nothing; kwargs...)
```

2-D グリッドファイルまたは GMTgrid タイプを読み込み、グリッドを通して各等高線をトレースすることによって等高線マップを生成します。

## パラメータ

  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは 15x10 cm の線形（非投影）マップです。
  * **A** | **annot** | **annotation** :: [Type => Str or Number]       $Arg = [-|[+]annot_int][labelinfo]$

    *annot_int* はデータ単位での注釈間隔です。等高線レベルがファイルで指定されている場合は無視されます。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **C** | **cont** | **contour** | **contours** | **levels** :: [Type => Str | Number | GMTcpt]  $Arg = [+]cont_int$

    描画する等高線は、3つの可能な方法のいずれかで指定できます。
  * **D** | **dump** :: [Type => Str]

    等高線をデータラインセグメントとしてダンプします。プロットは行われません。
  * **F** | **force** :: [Type => Str | []]

    ダンプされた等高線を強制的に、より高い z 値が左 (-Fl [デフォルト]) または右になるように向けます。
  * **G** | **labels** :: [Type => Str]

    引用された線に沿ったラベルの配置を制御します。
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **L** | **range** :: [Type => Str]

    範囲を制限します：低い値未満または高い値を超えるデータ値の等高線は描画しません。
  * **N** | **fill** | **colorize** :: [Type => Bool]

    cpt によって与えられた離散的なカラーテーブルを使用して、等高線の間の領域を塗りつぶします。
  * **P** | **portrait** :: [Type => Bool or []]

    GMT にポートレートモードで描画しないように指示します（つまり、ランドスケーププロットを作成します）。
  * **Q** | **cut** :: [Type => Str | Number]

    カット数未満のポイントを持つ等高線は描画しません。
  * **S** | **smooth** :: [Type => Number]

    等高線をおおよそ (gridbox_size/smoothfactor) 間隔で再サンプリングするために使用されます。
  * **T** | **ticks** :: [Type => Str]

    最も内側の閉じた等高線に沿って、*gap* ごとに下向きの方向を指す目盛りを描画します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    プロットに GMT タイムスタンプロゴを描画します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートを stderr に送信する冗長性レベルを選択します。
  * **W** | **pen** :: [Type => Str | Number]

    特定の線の属性を設定します。
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    プロットの原点を現在の原点に対して (x-shift,y-shift) だけシフトし、オプションで長さの単位 (c, i, または p) を追加します。
  * **Z** | **muladd** | **scale** :: [Type => Str]

    データからシフトを引き、等高線描画が始まる前に結果を因子で乗算するために使用します。
  * **bo** | **binary_out** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    ネイティブバイナリ出力を選択します。
  * **do** | **nodata_out** :: [Type => Str or Number]     $Arg = nodata$

    すべての出力列を調べ、任意の項目が NAN に等しい場合は、選択した欠損データ値で置き換えます。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含む ASCII データレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータタイプ（時間または地理データ）を指定します。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにはヘッダーレコードがあります。
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    視点の視点を選択し、方位角と高度を設定します [180/90]。
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    オーバーレイの PDF 透明度レベルを (0-100] パーセント範囲で設定します。[デフォルトは 0、すなわち不透明]。
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext` で図を保存します。ここで `ext` は図の形式を選択します（例：figname="name.png"）

完全なドキュメントを見るには、次のように入力してください：$@? grdcontour$ ```
