```
plot(arg1::Array; kwargs...)
```

は、ファイル [または標準入力] から (x,y) ペアを読み込み、地図上のその位置に線、ポリゴン、またはシンボルをプロットする PostScript コードを生成します。

完全な GMT ( `GMT.jl` ではない) ドキュメントは [`psxy`](http://docs.generic-mapping-tools.org/latest/plot.html) を参照してください。

## パラメータ

  * **A** | **steps** | **stairs** | **straight_lines** :: [Type => Str]

```
デフォルトでは、地理的な線分は大円弧として描画されます。
それらを直線として描画するには、このオプションを使用します。
```

  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影法を選択します。デフォルトは 15x10 cm の線形 (非投影) 地図です。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    CPT 名を指定するか、-Ccolor1,color2[,color3,...] を指定して、これらの色から自動的に線形連続 CPT を構築します。
  * **D** | **shift** | **offset** :: [Type => Str]

    指定された量 dx/dy でプロットシンボルまたは線の位置をオフセットします (cm、インチ、またはポイント)。
  * **E** | **error** | **error_bars** :: [Type => Str]

    対称エラーバーを描画します。
  * **F** | **conn** | **connection** :: [Type => Str]

    点の接続方法を変更します。
  * **G** | **fill** | **markerfacecolor** | **MarkerFaceColor** | **markercolor** | **mc** :: [Type => Str]

    シンボルまたはポリゴンの塗りつぶしの色またはパターンを選択します。ただし警告: エイリアス 'fill' はポリゴンまたはシンボルの色を設定しますが、両方を同時に設定することはできません。プロットにポリゴンとシンボルがある場合は、ポリゴンには 'fill' を、シンボルの塗りつぶしには 'markerfacecolor' を使用してください。以下の W にも同様のことが当てはまります。
  * **I** | **intens** :: [Type => Str | number]

    提供された強度値 ([-1 1] 範囲内) を使用して、照明をシミュレートすることによって塗りつぶしの色を変調します。
  * **L** | **close** | **polygon** :: [Type => Str]

    閉じたポリゴンを強制します。
  * **N** | **no_clip** | **noclip** :: [Type => Str or []]

    地図の境界の外にあるシンボルをクリップしないでください。
  * **P** | **portrait** :: [Type => Bool or []]

    GMT にポートレートモードで描画しないように指示します (つまり、ランドスケーププロットを作成します)。
  * **S** | **symbol** | **marker** | **Marker** :: [Type => Str]

    シンボルをプロットします (ベクトル、パイのスライス、前線、装飾されたまたは引用された線を含む)。代わりに、エイリアス: **marker** または **Marker** と値を使用してシンボルのサブセットを選択します:

      * **-**, **x_dash**
      * **+**, **plus**
      * **a**, *, **star**
      * **c**, **circle**
      * **d**, **diamond**
      * **g**, **octagon**
      * **h**, **hexagon**
      * **i**, **v**, **inverted_tri**
      * **n**, **pentagon**
      * **p**, **.**, **point**
      * **r**, **rectangle**
      * **s**, **square**
      * **t**, **^**, **triangle**
      * **x**, **cross**
      * **y**, **y_dash**

    そして、**markersize** または **size** キーワードでサイズを選択します [デフォルトは 7p]。マーカーサイズはスカラーまたはデータの行数と同じサイズのベクトルにすることができます。単位は、特に指定がない限りポイントです (例えば cm の場合) *par=(PROJ*LENGTH*UNIT="c")*。
  * **W** | **pen** | **markeredgecolor** | **mec** :: [Type => Str]

    線またはシンボルのアウトラインのペン属性を設定します。警告: ペン属性はポリゴンまたはシンボルのペンを設定しますが、両方を同時に設定することはできません。プロットにポリゴンとシンボルがある場合は、ポリゴンには **W** または **pen** を、シンボルの塗りつぶしには **markeredgecolor** を使用してください。上記の S と同様です。
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    プロットに GMT タイムスタンプロゴを描画します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートを stderr に送信する冗長性レベルを選択します。
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    プロットの原点を現在の原点に対して (x-shift,y-shift) だけシフトし、オプションで長さ単位 (c、i、または p) を追加します。
  * **Z** | **level** :: [Type => Str | NamedTuple]	`Arg = value|file[+f|+l] | (data=Array|Number, outline=_, fill=_)`

    指定されたレベルの後にポリゴンを塗りつぶします。これは、ポリゴンの数と同じサイズのベクトルまたは定数として指定する必要があります。カラーマップが必要です。
  * **aspect** :: [Type => Str]

    "equal" に等しい場合、正方形のプロットを作成します。
  * **a** | **aspatial** :: [Type => Str]			$Arg = [col=]name[…]$

    入力および出力中の GMT における非空間データの処理方法を制御します。
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    プライマリ入力のネイティブバイナリ形式を選択します (セカンダリ入力は常に ASCII です)。
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    すべての入力列を調べ、任意の項目が nodata と等しい場合、この値を欠損データ項目として解釈し、NaN で置き換えます。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含む ASCII データレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します (時間または地理データ)。
  * **g** | **gap** :: [Type => Str]           $Arg = [a]x|y|d|X|Y|D|[col]z[+|-]gap[u]$

    連続するデータポイント間の間隔を調べ、線にブレークを課すために使用します。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにはヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    プライマリ入力の特定のデータ列を任意の順序で選択します。
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    視点の視点を選択し、方位角と高度を設定します [180/90]。
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    オーバーレイの PDF 透明度レベルを設定します (0-100] パーセント範囲。 [デフォルトは 0、すなわち不透明]。
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    入力レコードを循環座標に変換します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で 1 列目と 2 列目を入れ替えます。
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext` で図を保存します。ここで `ext` は図の形式を選択します (例: figname="name.png")。
