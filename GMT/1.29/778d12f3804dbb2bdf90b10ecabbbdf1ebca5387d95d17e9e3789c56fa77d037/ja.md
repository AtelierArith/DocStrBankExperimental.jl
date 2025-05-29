```
meca(cmd0::String="", arg1=nothing; kwargs...)
```

焦点メカニズムをプロットします。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`meca`](http://docs.generic-mapping-tools.org/latest/supplements/seis/meca.html)を参照してください。

## パラメータ

  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは15x10 cmの線形（非投影）マップです。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある地域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **A** | **offset** :: [Type => Bool | Str | GMTcpt]

    入力の最後の2列に指定された経度、緯度に焦点メカニズムをオフセットします。
  * **C** | **color** | **cmap** :: [Type => Number | Str | GMTcpt]

    CPTを指定し、圧縮部分の色を3列目のz値によって決定させます。
  * **D** | **depth_limits** :: [Type => Str | Tuple]

    depminとdepmaxの間のイベントをプロットします。
  * **E** | **fill_extensive** | **extensionfill** :: [Type => Str | Number]

    拡張四分円の塗りつぶしを選択します。[デフォルトは白です]。
  * **Fa** | **Fe** | **Fg** | **Fo** | **Fp** | **Fr** | **Ft** | **Fz** :: [Type => ]

    1つ以上の属性を設定します。
  * **G** | **fill** | **compressionfill** :: [Type => Str | Number]

    セクターの塗りつぶしのためのシェード、色、またはパターンを選択します。[デフォルトは塗りつぶしなしです]。
  * **P** | **portrait** :: [Type => Bool or []]

    GMTにポートレートモードで描画しないように指示します（つまり、ランドスケーププロットを作成します）。
  * **L** | **outline_pen** | **pen_outline** :: [Type => Str | Number | Tuple]

    デフォルトのペンでなく、ペン属性を使用して「ビーチボール」のアウトラインを描画します。
  * **M** | **same_size** | **samesize** :: [Type => Bool]

    すべてのマグニチュードに同じサイズを使用します。サイズは**S**で指定されます。
  * **N** | **no_clip** | **noclip** :: [Type => Str | []]

    フレームの境界外にあるシンボルをスキップしません。
  * **Sc|aki** | **Sc|CMT|gcmt** | **Sm|mt|moment_tensor** | ... :: [Type => Str]

    入力データの列の意味を選択します。
  * **convention=:Sa|:aki|:Sc|:CMT|:gcmt|:Sm|:mt|:moment*tensor|:Sd|:mt*closest|:moment*closest|:Sz|:mt*deviatoric :moment*deviatoric|:Sp :partial|:Sx|:principal|:principal*axis|:Sy|:principal*closest|:St|:principal*deviatoric

    入力データの列の意味を選択する別の方法です。
  * **T** | **nodal** :: [Type => Number | Str]

    ノード面をプロットし、透明なバブルのアウトラインを描画します。
  * **W** | **pen** :: [Type => Str | Tuple]

    すべての線とシンボルのアウトラインのためのペン属性を設定します。
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    プロットにGMTタイムスタンプロゴを描画します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告をstderrに送信する冗長性レベルを選択します。
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    プロットの原点を現在の原点に対して(x-shift,y-shift)だけシフトし、オプションで長さ単位(c, i, または p)を追加します。
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    すべての入力列を調べ、任意の項目がnodataと等しい場合、この値を欠損データ項目として解釈し、NaNで置き換えます。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含むASCIIデータレコードのみを受け入れます。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにはヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    プライマリ入力の特定のデータ列を任意の順序で選択します。
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    視点の視点を選択し、方位角と高度を設定します[x|y|z]。
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    オーバーレイのPDF透明度レベルを(0-100]パーセント範囲で設定します。[デフォルトは0、すなわち不透明です]。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

例：Aki & Richardsの慣習を使用して焦点メカニズムをプロットする

```julia
    psmeca([0.0 3.0 0.0 0 45 90 5 0 0], aki=true, fill=:black, region=(-1,4,0,6), proj=:Merc, show=1)
```

同じですが、ラベルを追加します

```julia
    psmeca(mat2ds([0.0 3.0 0.0 0 45 90 5 0 0], ["Thrust"]), aki=true, fill=:black, region=(-1,4,0,6), proj=:Merc, show=1)
```
