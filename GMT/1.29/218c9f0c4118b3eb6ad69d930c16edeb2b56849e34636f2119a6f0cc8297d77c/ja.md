```
gmtselect(cmd0::String="", arg1=nothing, kwargs...)
```

複数の空間基準に基づいてデータテーブルのサブセットを選択します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`gmtselect`](http://docs.generic-mapping-tools.org/latest/gmtselect.html)を参照してください。

## パラメータ

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある地域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **A** | **area** :: [Type => Str | Number]

    面積がmin*area（km^2）未満の特徴や、階層レベルがmin*levelより低いかmax_levelより高いものはプロットされません。
  * **C** | **dist2pt** | **dist** :: [Type => Str | NamedTuple]   `Arg = pointfile+ddist[unit] | (pts=Array, dist=xx)`

    ASCIIファイルpointfile内の任意のポイントからdist以内に位置するすべてのレコードを渡します。distがゼロの場合、pointfileの3列目には各ポイントの影響半径が必要です。
  * **D** | **res** | **resolution** :: [Type => Str]      `Arg = c|l|i|h|f`

    Nが設定されていない限り無視されます。使用する海岸線データセットの解像度を選択します（(f)ull, (h)igh, (i)ntermediate, (l)ow, または (c)rude）。
  * **E** | **boundary** :: [Type => Str | []]            `Arg = [fn]`

    ポリゴン境界上のポイントをどのように扱うかを指定します。
  * **F** | **polygon** :: [Type => Str | GMTdaset | Mx2 array]     `Arg = polygonfile`

    複数セグメントファイル$polygonfile$内の閉じたポリゴンのいずれかに位置するすべてのレコードを渡します。または、ポリゴンを定義するGMTdataset型またはMx2配列。
  * **G** | **gridmask** :: [Type => Str | GRDgrid]        `Arg = gridmask`

    グリッドgridmaskの有効データ領域内にあるすべての位置を渡します。外部のノードはNaNまたはゼロです。
  * **I** | **invert** | **reverse** :: [Type => Str | []]    `Arg = [cflrsz]`

    指定された各基準のテストの意味を反転させます。
  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは15x10 cmの線形（非投影）地図です。
  * **L** | **dist2line** :: [Type => Str | NamedTuple]    `Arg = linefile+ddist[unit][+p] | (pts=Array, dist=xx, ortho=_)`

    ASCII複数セグメントファイルlinefile内の任意の線分からdist以内に位置するすべてのレコードを渡します。
  * **N** | **mask** :: [Type => Str | List]     `Arg = ocean/land/lake/island/pond or wet/dry`

    指定された地理的特徴内に位置するすべてのレコードを渡します。
  * **Z** | **in_range** :: [Type => Str | List]     `Arg = min[/max][+a][+ccol][+i]`

    3列目（z; col = 2）が指定された範囲内にあるかNaNであるすべてのレコードを渡します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告をstderrに送信する冗長性レベルを選択します。
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    結果をJulia変数に戻すのではなく、ASCIIファイルに保存します。ファイル名を引数として指定します。boオプションを使用してバイナリファイルとして保存します。
  * **append** :: [Type => Str]     $Arg = fname$

    結果をJulia変数に戻すのではなく、$fname$という既存のファイルに追加します。boオプションを使用してバイナリファイルとして保存します。
  * **b** | **binary** :: [Type => Str]
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    ユーザーがコーディングした欠損データ値がGMTの公式NaN値にどのように変換されるかを制御します。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含むASCIIデータレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します（時間または地理データ）。
  * **g** | **gap** :: [Type => Str]           $Arg = [a]x|y|d|X|Y|D|[col]z[+|-]gap[u]$

    連続データポイント間の間隔を調べて、線の中断を課します。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    主な入力ファイルにはヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    主な入力の特定のデータ列を任意の順序で選択します。
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    主な出力の特定のデータ列を任意の順序で選択します。
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    入力レコードを循環座標に変換します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。
