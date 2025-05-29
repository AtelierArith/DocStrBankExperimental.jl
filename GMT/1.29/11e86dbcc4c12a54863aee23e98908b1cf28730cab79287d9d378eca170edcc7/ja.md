```
image(cmd0::String="", arg1=nothing; kwargs...)
```

地図に画像またはEPSファイルを配置します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`psimage`](http://docs.generic-mapping-tools.org/latest/image.html)を参照してください。

## パラメータ

  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **D** | **pos** | **position** :: [Type => Str]

    4つの座標系のいずれかを使用して、画像の地図上の基準点を設定します。
  * **F** | **box** :: [Type => Str | []]

    追加のオプションなしで、画像の周りにMAP*FRAME*PENを使用して矩形の境界を描画します。
  * **G** | **bitcolor** | **bit_color** | **bit_bg|fg|alpha**:: [Type => Str]

    特定のピクセル値を別の色に変更するか、透明にします。
  * **I** | **invert** :: [Type => Str | Number]

    プロットする前に1ビット画像を反転させます。
  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは15x10 cmの線形（非投影）地図です。
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **M** | **monochrome** :: [Type => Bool]

    カラー画像を（テレビ）YIQ変換を使用してモノクロのグレースケールに変換します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    プロットにGMTタイムスタンプロゴを描画します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    プロットの原点を現在の原点に対して(x-shift,y-shift)だけシフトし、オプションで長さの単位(c, i, または p)を追加します。
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    視点の透視図を選択し、視点の方位角と高度を設定します[180/90]。
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    オーバーレイのPDF透明度レベルを(0-100]パーセント範囲で設定します。[デフォルトは0、すなわち不透明]。
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext`で図を保存します。ここで`ext`は図の形式を選択します（例：figname="name.png"）。

完全なドキュメントを見るには、次のように入力します: $@? image$
