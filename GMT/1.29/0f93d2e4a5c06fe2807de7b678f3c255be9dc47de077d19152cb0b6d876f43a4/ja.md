```
mapproject(cmd0::String="", arg1=nothing, kwargs...)
```

前方および逆の地図変換、データム変換および測地学。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`mapproject`](http://docs.generic-mapping-tools.org/latest/mapproject.html)を参照してください。

## パラメータ

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある地域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **J** | **proj** | **projection** :: [Type => String]

    地図投影を選択します。デフォルトは15x10 cmの線形（非投影）地図です。
  * **A** | **azim**  | **azimuth**:: [Type => Str]    $Arg = b|B|f|F|o|O[lon0/lat0][+v]$

    トラックに沿った方位角またはlon0/lat0で設定されたオプションの固定点への方位角を計算します。
  * **C** | **center** :: [Type => Str | List | []]     $Arg = [dx/dy]$

    投影座標の中心を地図投影の中心に設定します [デフォルトは左下隅]。
  * **D** | **lengthunit** :: [Type => Str]    $Arg = c|i|p$

    PROJ*LENGTH*UNITを一時的にオーバーライドし、c（cm）、i（インチ）、またはp（ポイント）を使用します。
  * **E** | **geod2ecef** | **ecef** :: [Type => Str | []]    $Arg = [datum]$

    測地（lon, lat, height）から地球中心地球固定（ECEF）（x,y,z）座標に変換します。
  * **F** | **one2one** :: [Type => Str | []]    $Arg = [unit]$

    1:1スケーリングを強制します。つまり、出力（または入力、Iを参照）データは実際の投影メートルである必要があります。
  * **G** | **track_distances** :: [Type => Str | List]    $Arg = [lon0/lat0][+a][+i][+u[+|-]unit][+v]$

    トラックに沿った距離またはG="lon0/lat0"で設定されたオプションの固定点への距離を計算します。
  * **I** | **inverse** :: [Type => Bool]

    逆変換を行います。つまり、(x,y)データから(経度, 緯度)を取得します。
  * **L** | **dist2line** :: [Type => Str | NamedTuple]   $Arg = line.xy[+u[+|-]unit][+p] | (line=Matrix, unit=x, fractional_pt=_,cartesian=true, projected=true)$

    入力データポイントからASCIIマルチセグメントファイルline.xyに指定された線への最短距離を決定します。
  * **N** | **geod2aux** :: [Type => Str | []]       $Arg = [a|c|g|m]$

    測地緯度から4つの異なる補助緯度のいずれかに変換します（経度には影響しません）。
  * **Q** | **list** :: [Type => Str | []]           $Arg = [d|e]$

    すべての投影パラメータをリストします。データムのみをリストするにはQ=:dを使用し、楕円体のみをリストするにはQ=:eを使用します。
  * **S** | **supress** :: [Type => Bool]

    地域外にあるポイントを抑制します。
  * **T** | **change_datum** :: [Type => Str]    $Arg = [h]from[/to]$

    標準のモロデンスキー変換を使用して、データム間の座標変換を行います。
  * **W** | **map_size** | **mapsize** :: [Type => Str | []]    $Arg = [w|h]$

    標準出力に地図の幅と高さを印刷します。入力ファイルは読み込まれません。
  * **Z** | **traveltime** | **travel_times** :: [Type => Str | Number]    $Arg = [speed][+a][+i][+f][+tepoch]$

    -Gで指定されたトラックに沿った移動時間を計算します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **b** | **binary** :: [Type => Str]
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    ユーザーがコーディングした欠損データ値がGMTの公式NaN値にどのように変換されるかを制御します。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含むASCIIデータレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します（時間または地理データ）。
  * **g** | **gap** :: [Type => Str]           $Arg = [a]x|y|d|X|Y|D|[col]z[+|-]gap[u]$

    連続するデータポイント間の間隔を調べて、線にブレークを課すようにします。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    プライマリ入力の特定のデータ列を任意の順序で選択します。
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    プライマリ出力の特定のデータ列を任意の順序で選択します。
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    視点の視点を選択し、方位角と高度を設定します [180/90]。
  * **s** | **skiprows** | **skip_NaN** :: [Type => Str]       $Arg = [cols][a|r]$

    z値がNaNに等しいレコードの出力を抑制します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

完全なドキュメントを見るには、次のように入力してください: $@? mapproject$
