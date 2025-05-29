```
wiggle(cmd0::String="", arg1=nothing; kwargs...)
```

ファイルから (length,azimuth) ペアを読み取り、風のウィグル図をプロットします。

完全な GMT ( `GMT.jl` ではない) ドキュメントは [`pswiggle`](http://docs.generic-mapping-tools.org/latest/wiggle.html) を参照してください。

## パラメータ

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **Z** | **ampscale** | **amp_scale** :: [Type => Number | Str]

    データ単位/距離単位での異常スケールを提供します。
  * **A** | **azimuth** :: [Type => Str | number]

    好ましい正の方位を設定します。正のウィグルはその方向に「引き寄せられます」。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **C** | **center** :: [Type => Number]

    プロットする前にデータセットから中心を引きます [0]。
  * **D** | **scale_bar** :: [Type => Str]

    垂直スケールバーの地図上の基準点を定義します。
  * **F** | **box** :: [Type => Str]

    さらなるオプションなしで、垂直スケールバーの周りに長方形の境界を描きます。
  * **G** | **fill** :: [Type => Number | Str]

    正のウィグルおよび/または負のウィグルの塗りつぶしの色、色合い、またはパターンを設定します [デフォルトは塗りつぶしなし]。
  * **I** | **fixed_azim** :: [Type => Number]

    ウィグルの固定方位投影を設定します [デフォルトはトラック方位を使用しますが、-Aを参照してください]。
  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは 15x10 cm の線形 (非投影) 地図です。
  * **P** | **portrait** :: [Type => Bool or []]

    GMT にポートレートモードで描画しないように指示します (つまり、ランドスケーププロットを作成します)。
  * **T** | **track** :: [Type => Number or Str | Tuple | []]

    トラックを描画します [デフォルトはトラックなし]。使用するペンの属性を追加します [デフォルト: width = 0.25p, color = black, style = solid]。
  * **W** | **pen** :: [Type => Number | Str | tuple | []]

    アウトラインペンの属性を指定します [デフォルトはアウトラインなし]。
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    プロットに GMT タイムスタンプロゴを描画します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートを stderr に送信する冗長性レベルを選択します。
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    プロットの原点を現在の原点に対して (x-shift,y-shift) だけシフトし、オプションで長さ単位 (c, i, または p) を追加します。
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    プライマリ入力のネイティブバイナリ形式を選択します (セカンダリ入力は常に ASCII です)。
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    すべての入力列を調べ、任意の項目が nodata と等しい場合、この値を欠損データ項目として解釈し、値 NaN に置き換えます。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含む ASCII データレコードのみを受け入れます。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    プライマリ入力の特定のデータ列を任意の順序で選択します。
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    視点の視点を選択し、方位と高度を設定します [180/90]。
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    オーバーレイの PDF 透明度レベルを (0-100] パーセント範囲で設定します。 [デフォルトは 0、すなわち不透明]。
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    入力レコードを循環座標に変換します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で 1 列目と 2 列目を入れ替えます。
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext` で図を保存します。ここで `ext` は図の形式を選択します (例: figname="name.png")

完全なドキュメントを見るには、次のように入力してください: $@? pswiggle$
