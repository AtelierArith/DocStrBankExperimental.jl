```
project(cmd0::String="", arg1=nothing, kwargs...)
```

データを線または大円に投影し、トラックを生成するか、座標を変換します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`project`](http://docs.generic-mapping-tools.org/latest/project.html)を参照してください。

## パラメータ

  * **C** | **origin** | **start_point** :: [Type => list/tuple]    $Arg = (x,y)$

    投影の原点を定義します（定義1または2）。
  * **A** | **azim** | **azimuth** :: [Type => Number]    $Arg = azimuth$

    投影の方位角を定義します（定義1）。
  * **E** | **end_pt** | **endpoint** :: [Type => list/tuple]    $Arg = (bx,by)$

    bx,byは投影パスの終点を定義します（定義2）。
  * **F** | **outvars** :: [Type => Str]    $Arg = xyzpqrs$

    xyzpqrsの任意の組み合わせを使用して、希望する出力を指定します（順序は任意）[デフォルトはxyzpqrs]。
  * **G** | **step** | **generate** :: [Type => Number or list/tuple–    $Arg = dist[/colat][+h]$

    生成モード。入力は読み取られません。pの各dist単位ごとに(r, s, p)出力点を作成します。Qオプションを参照してください。
  * **L** | **length** :: [Type => Number or list/tuple]    $Arg = [w|l_{min}/l_{max}]$

    長さ制御。p座標がl*min < p < l*maxの範囲内にある点のみを投影します。
  * **N** | **flat_earth** :: [Type => Bool or []]

    平面地球。平面での直交座標変換を行います。[デフォルトは球面三角法を使用します。]
  * **Q** | **km** :: [Type => Bool or []]

    地図タイプの単位。
  * **S** | **sort** :: [Type => Bool or []]

    出力をpの増加順にソートします。ランダムデータを順次プロファイルに投影する際に便利です。
  * **T** | **pole** :: [Type => list/tuple]    $Arg = (px,py)$

    px,pyは投影の回転極の位置を設定します（定義3）。
  * **W** | **width** :: [Type => list/tuple]    $Arg = (w_{min},w_{max})$

    幅制御。q座標がw*min < q < w*maxの範囲内にある点のみを投影します。
  * **Z** | **ellipse** :: [Type => Number | Tuple | String]    $Arg = major/minor/azimuth[+e|n]$

    kmで与えられた主軸と副軸を持つ楕円を作成します（**N**が与えられた場合は直交楕円）。主軸の方位角は度で指定され、**origin**（中心を設定）および**step**（距離の増分を設定）と組み合わせて使用されます。
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    結果をJulia変数に戻すのではなく、ASCIIファイルに保存します。ファイル名を引数として指定します。boオプションを使用してバイナリファイルとして保存します。
  * **append** :: [Type => Str]     $Arg = fname$

    結果をJulia変数に戻すのではなく、$fname$という名前の既存のファイルに追加します。boオプションを使用してバイナリファイルとして保存します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告をstderrに送信する冗長性レベルを選択します。
  * **b** | **binary** :: [Type => Str]
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    ユーザーがコーディングした欠損データ値がGMTの公式NaN値にどのように変換されるかを制御します。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含むASCIIデータレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します（時間または地理データ）。
  * **g** | **gap** :: [Type => Str]           $Arg = [a]x|y|d|X|Y|D|[col]z[+|-]gap[u]$

    連続データポイント間の間隔を調べて、線にブレークを課します。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    プライマリ入力の特定のデータ列を任意の順序で選択します。
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    プライマリ出力の特定のデータ列を任意の順序で選択します。
  * **s** | **skiprows** | **skip_NaN** :: [Type => Str]       $Arg = [cols][a|r]$

    z値がNaNに等しいレコードの出力を抑制します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

完全なドキュメントを見るには、次のように入力してください: $@? project$
