```
bar3(cmd0::String="", arg1=nothing; kwargs...)
```

グリッドファイル、グリッド、またはMxN行列を読み込み、基準からzまで延びる垂直バーをプロットします。

  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは15x10 cmの線形（非投影）地図です。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある地域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **fill** :: [Type => Str]		$key=color$

    バーの塗りつぶしに使用する色またはパターンを選択します。
  * **base** :: [Type => Str | Num]		$key=value$

    デフォルトでは、base = yminです。このオプションを使用してその値を変更します。baseが追加されていない場合は、読み取ります。
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    視点の視覚的な見方を選択し、視点の方位角と高度を設定します [180/90]。
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext`で図を保存します。ここで`ext`は図の形式を選択します（例：figname="name.png"）。

例:

```
G = gmt("grdmath -R-15/15/-15/15 -I0.5 X Y HYPOT DUP 2 MUL PI MUL 8 DIV COS EXCH NEG 10 DIV EXP MUL =");
bar3(G, lw=:thinnest, show=true)
```
