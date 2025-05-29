```
contour(cmd0::String="", arg1=nothing; kwargs...)
```

テーブルデータを読み込み、三角形分割によって生の等高線プロットを生成します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`contour`](http://docs.generic-mapping-tools.org/latest/contour.html)を参照してください。

## パラメータ

  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは15x10 cmの線形（非投影）地図です。
  * **A** | **annot** | **annotation** :: [Type => Str | Number]       $Arg = [-|[+]annot_int][labelinfo]$

    *annot_int*はデータ単位での注釈間隔です。等高線レベルがファイルに指定されている場合は無視されます。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **C** | **cont** | **contour** | **contours** | **levels** :: [Type => Str | Number | GMTcpt]  $Arg = [+]cont_int$

    描画される等高線は、3つの可能な方法のいずれかで指定できます。
  * **D** | **dump** :: [Type => Str]

    等高線をデータラインセグメントとしてダンプします。プロットは行われません。
  * **E** | **index** :: [Type => Str | Mx3 array]

    ネットワーク情報を含むファイルの名前を指定します。各レコードは三角形のノード番号の三つ組を含む必要があります。
  * **G** | **labels** :: [Type => Str]

    引用された線に沿ったラベルの配置を制御します。
  * **I** | **fill** | **colorize** :: [Type => Bool]

    **C**を介して提供されたカラースケールを使用して三角形に色を付けます。
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **L** | **mesh** :: [Type => Str | Number]

    指定されたペン属性を使用して基礎となる三角形メッシュを描画します（提供されていない場合はデフォルトのペンを使用）。
  * **N** | **no_clip** :: [Type => Bool]

    境界で等高線や画像をクリップしないでください [デフォルトは領域内に収まるようにクリップします]。
  * **P** | **portrait** :: [Type => Bool or []]

    GMTにポートレートモードで描画しないように指示します（つまり、ランドスケーププロットを作成します）。
  * **Q** | **cut** :: [Type => Str | Number]         $Arg = [cut[unit]][+z]]$

    点数がcut未満の等高線を描画しません。
  * **S** | **skip** :: [Type => Str | []]            $Arg = [p|t]$

    領域の外にあるすべての入力xyzポイントをスキップします。
  * **T** | **ticks** :: [Type => Str]                 $Arg = [+|-][+a][+dgap[/length]][+l[labels]]$

    最も内側の閉じた等高線に沿って、*gap*ごとに下向きの目盛りを描画します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    プロットにGMTタイムスタンプロゴを描画します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **W** | **pen** :: [Type => Str | Number]

    特定の線の属性を設定します。
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    プロットの原点を現在の原点に対して(x-shift,y-shift)だけシフトし、オプションで長さ単位(c, i, または p)を追加します。
  * **Z** | **scale** :: [Type => Str]

    データからシフトを引き、等高線を描画する前に結果を因子で乗算するために使用します。
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    プライマリ入力のネイティブバイナリ形式を選択します（セカンダリ入力は常にASCIIです）。
  * **bo** | **binary_out** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    ネイティブバイナリ出力を選択します。
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    ユーザーがコーディングした欠損データ値がGMTの公式NaN値にどのように変換されるかを制御します。
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    すべての入力列を調べ、任意の項目がnodataに等しい場合、この値を欠損データ項目として解釈し、NaNで置き換えます。
  * **do** | **nodata_out** :: [Type => Str or Number]     $Arg = nodata$

    すべての出力列を調べ、任意の項目がNANに等しい場合、それを選択した欠損データ値で置き換えます。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含むASCIIデータレコードのみを受け入れます。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにはヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    プライマリ入力の特定のデータ列を任意の順序で選択します。
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    視点の視点を選択し、方位角と高度を設定します [180/90]。
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    オーバーレイのPDF透明度レベルを(0-100]パーセント範囲で設定します。[デフォルトは0、すなわち不透明]。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext`で図を保存します。ここで`ext`は図の形式を選択します（例：figname="name.png"）

完全なドキュメントを見るには、次のように入力してください: $@? contour$
