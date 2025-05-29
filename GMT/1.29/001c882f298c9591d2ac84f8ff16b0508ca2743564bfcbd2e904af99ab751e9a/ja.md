```
contourf(cmd0::String="", arg1=nothing; kwargs...)
```

x,y[,z]データに対してデローニ三角分割を実行します。つまり、点がどのように接続されるべきかを見つけて、可能な限り最も等辺の三角形分割を提供します。

完全なGMT（`GMT.jl`ではない）ドキュメントは、[`triangulate`](http://docs.generic-mapping-tools.org/latest/triangulate.html)を参照してください。

## パラメータ

  * **A** | **annot** :: [Type => Str | Number]       $Arg = [-|[+]annot_int][labelinfo]$

    *annot_int*はデータ単位での注釈間隔です。等高線レベルがファイルに指定されている場合は無視されます。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **C** | **cont** | **contour** | **contours** | **levels** :: [Type => Str | Number | GMTcpt]  $Arg = [+]cont_int$

    描画される等高線は、3つの可能な方法のいずれかで指定できます。
  * **E** | **index** :: [Type => Str | Mx3 array]

    ネットワーク情報を含むファイルの名前を指定します。各レコードは三角形のノード番号の三つ組を含む必要があります。
  * **G** | **labels** :: [Type => Str]

    引用された線に沿ったラベルの配置を制御します。
  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは15x10 cmの線形（非投影）地図です。
  * **P** | **portrait** :: [Type => Bool or []]

    GMTにポートレートモードで描画しないように指示します（つまり、ランドスケーププロットを作成します）。
  * **Q** | **cut** :: [Type => Str | Number]         $Arg = [cut[unit]][+z]]$

    点の数がcut未満の等高線は描画しません。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **S** | **skip** :: [Type => Str | []]            $Arg = [p|t]$

    領域の外にあるすべての入力xyzポイントをスキップします（入力データがテーブルの場合に使用されます）。
  * **S** | **smooth** :: [Type => Number]

    等高線を約（gridbox_size/smoothfactor）間隔で再サンプリングするために使用されます。（入力データがグリッドの場合に使用されます）
  * **T** | **ticks** :: [Type => Str]                 $Arg = [+|-][+a][+dgap[/length]][+l[labels]]$

    最も内側の閉じた等高線に沿って*gap*ごとに下向きの方向を指す目盛りを描画します。
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    プロットにGMTタイムスタンプロゴを描画します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **W** | **pen** :: [Type => Str | Number]

    特定の線の属性を設定します。
  * **Z** | **xyz** | **triplets** :: [Type => Bool]
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    主入力のネイティブバイナリ形式を選択します（副入力は常にASCIIです）。
  * **bo** | **binary_out** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    ネイティブバイナリ出力を選択します。
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    すべての入力列を調べ、任意の項目がnodataに等しい場合、この値を欠損データ項目として解釈し、NaNで置き換えます。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含むASCIIデータレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します（時間または地理データ）。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    主入力ファイルにはヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    主入力の特定のデータ列を任意の順序で選択します。
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    視点の方位角と高度を設定し、視点のパースペクティブビューを選択します [180/90]。
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    オーバーレイのPDF透明度レベルを(0-100]パーセント範囲で設定します。[デフォルトは0、すなわち不透明]。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

## 例

```julia
    G = GMT.peaks();
    C = makecpt(T=(-7,9,2));

    contourf(G, show=1)
    contourf(G, C=[-2, 0, 2, 5], show=1)
    contourf(G, C, contour=[-2, 0, 2, 5], show=1)
    contourf(G, C, annot=[-2, 0, 2, 5], show=1)
    contourf(G, C, annot=2, show=1)
    contourf(G, C, contour=1, annot=[-2, 0, 2, 5], show=1)
    contourf(G, C, annot=:none, show=1)

    d = [0 2 5; 1 4 5; 2 0.5 5; 3 3 9; 4 4.5 5; 4.2 1.2 5; 6 3 1; 8 1 5; 9 4.5 5];
    contourf(d, limits=(-0.5,9.5,0,5), pen=0.25, labels=(line=(:min,:max),), show=1)
```
