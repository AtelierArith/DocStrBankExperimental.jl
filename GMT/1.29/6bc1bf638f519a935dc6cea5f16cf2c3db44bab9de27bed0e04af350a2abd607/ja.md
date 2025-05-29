```
logo(cmd0::String=""; kwargs...)
```

地図上にGMTロゴをプロットします。デフォルトでは、GMTロゴは幅5 cm、高さ2.5 cmで、現在のプロットの原点に対して配置されます。さまざまなオプションを使用してこれを変更し、GMTロゴの背後に透明または不透明な長方形の地図パネルを配置します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`gmtlogo`](http://docs.generic-mapping-tools.org/latest/gmtlogo.html)を参照してください。

## パラメータ

  * **D** | **pos** | **position** :: [Type => Str]

    画像の参照点を地図上に設定します。4つの座標系のいずれかを使用します。
  * **F** | **box** :: [Type => Str]

    さらなるオプションなしで、GMTロゴの周りに`MAP_FRAME_PEN`を使用して長方形の境界を描画します。 または地図のバラ (T)
  * **julia** :: [Type => Number]

    GMTロゴの代わりにJuliaを作成します。センチメートル単位で円の直径を指定します。
  * **GMTjulia** :: [Type => Number]

    GMT Julia GMTロゴを作成します。センチメートル単位で円の直径を指定します。
  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは15x10 cmの線形（非投影）地図です。
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **P** | **portrait** :: [Type => Bool or []]

    GMTにポートレートモードで描画しないように指示します（つまり、ランドスケーププロットを作成します）。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定します。
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    プロットにGMTタイムスタンプロゴを描画します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    プロットの原点を現在の原点に対して(x-shift,y-shift)だけシフトし、オプションで長さの単位（c, i, または p）を追加します。
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    オーバーレイのPDF透明度レベルを(0-100]パーセント範囲で設定します。[デフォルトは0、すなわち不透明]です。
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext`で図を保存します。ここで`ext`は図の形式を選択します（例：figname="name.png"）。
  * 例：1 cmの円を持つGMT Juliaロゴを作成します：logo(GMTjulia=1, show=true)
