```
legend(cmd0::String="", arg1=nothing; kwargs...)
```

地図上に重ねることができる凡例を作成します。入力またはファイルから特定の凡例関連情報を読み取ります。

完全なGMT（`GMT.jl`ではない）ドキュメントは、[`legend`](http://docs.generic-mapping-tools.org/latest/legend.html)を参照してください。

## パラメータ

  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは15x10 cmの線形（非投影）地図です。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある地域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **C** | **clearance** :: [Type => Str]

    凡例フレームと内部アイテムの間のクリアランスを設定します [4p/4p]。
  * **D** | **pos** | **position** :: [Type => Str]  `Arg=[g|j|J|n|x]refpoint+wwidth[/height][+jjustify][+lspacing][+odx[/dy]]`

    4つの座標系のいずれかを使用して、地図上の凡例の基準点を定義します。
  * **F** | **box** :: [Type => Str | Number]   `Arg=[+cclearances][+gfill][+i[[gap/]pen]][+p[pen]][+r[radius]][+s[[dx/dy/][shade]]]`

    さらなるオプションなしで、凡例の周りに矩形の境界を描画します *MAP*FRAME*PEN*を使用します。
  * **M** | **source** :: [Type => Bool]

    モダンモードのみ：
  * **S** | **scale** :: [Type => Number]

    すべてのシンボルサイズを共通のスケールでスケーリングします。
  * **T** | **leg_file** :: [Type => Str]

    モダンモードのみ：隠れた凡例仕様ファイルをfnameに書き込みます。
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **P** | **portrait** :: [Type => Bool or []]

    GMTにポートレートモードで描画しないように指示します（つまり、ランドスケーププロットを作成します）。
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    プロットにGMTタイムスタンプロゴを描画します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    プロットの原点を現在の原点に対して(x-shift,y-shift)だけシフトし、オプションで長さ単位(c, i, または p)を追加します。
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    視点の方位角と高度を設定し、透視図を選択します [180/90]。
  * **q** | **inrow** | **inrows** :: [Type => Str]       $Arg = [i|o][~]rows[+ccol][+a|f|s]$

    読み取る特定のデータ行を選択します（-qi [デフォルト]）または書き込みます（-qo） [すべて]。
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    オーバーレイのPDF透明度レベルを(0-100]パーセント範囲で設定します。[デフォルトは0、すなわち不透明]。
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext`で図を保存します。ここで`ext`は図の形式を選択します（例：figname="name.png"）

完全なドキュメントを見るには、次のように入力してください: $@? legend$ ```
