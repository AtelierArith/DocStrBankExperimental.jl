```
basemap(; kwargs...)
```

ベースマップとフレームをプロットします。

完全なGMT（`jl`のものではない）ドキュメントは[`psbasemap`](http://docs.generic-mapping-tools.org/latest/basemap.html)を参照してください。

## パラメータ

  * **J** | **proj** | **projection** :: [Type => String]

    マップ投影を選択します。デフォルトは15x10 cmの線形（非投影）マップです。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある地域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **A** | **polygon** :: [Type => Str | []]

    プロットは行われません。代わりに、（おそらく斜めの）長方形マップ領域のポリゴンの輪郭の地理座標を決定します。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    マップの境界フレームと軸の属性を設定します。
  * **inset** :: [Type => NamedTuple]

    マップ上にシンプルなマップ挿入ボックスを描画します。
  * **F** | **box** :: [Type => Str]

    さらなるオプションなしで、任意のマップ挿入（D）、マップスケール（L）またはマップローズ（T）の周りに長方形の境界を描画します。
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **L** | **map_scale** :: [Type => Str]

    マップスケールを描画します。
  * **P** | **portrait** :: [Type => Bool or []]

    GMTにポートレートモードで描画しないように指示します（つまり、ランドスケーププロットを作成します）。
  * **Td** | **rose** :: [Type => Str]

    参照点とアンカーポイントで定義された位置にマップ方向ローズを描画します。
  * **Tm** | **compass** :: [Type => Str]

    参照点とアンカーポイントで定義された位置にマップ磁気ローズを描画します。
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    プロットにGMTタイムスタンプロゴを描画します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    プロットの原点を現在の原点に対して（x-shift,y-shift）だけシフトし、オプションで長さ単位（c, i, または p）を追加します。
  * **bo** | **binary_out** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    ネイティブバイナリ出力を選択します。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型（時間または地理データ）を指定します。
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    視点のパースペクティブビューを選択し、方位角と高度を設定します [180/90]。
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    オーバーレイのPDF透明度レベルを（0-100]パーセント範囲で設定します。[デフォルトは0、すなわち不透明]。

完全なドキュメントを見るには、次のコマンドを入力してください: $@? basemap$
