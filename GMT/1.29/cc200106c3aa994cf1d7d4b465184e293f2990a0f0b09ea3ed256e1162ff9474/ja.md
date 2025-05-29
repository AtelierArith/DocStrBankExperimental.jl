```
regress(cmd0::String="", arg1=nothing, kwargs...)
```

1次元データセットの線形回帰。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`regress`](http://docs.generic-mapping-tools.org/latest/gmtregress.html)を参照してください。

## パラメータ

  * **A** | **all_slopes** :: [Type => Str | List]        $Arg = min/max/inc$

    最適な回帰を決定する代わりに、回帰の全範囲を探索します。
  * **C** | **ci** | **cl** | **confidence_level** :: [Type => Int]      $Arg = level$

    回帰の信頼区間のオプション計算に使用する信頼レベル（%）を設定します [95]。
  * **E** | **regression_type** :: [Type => Str]   $Arg = x|y|o|r$

    線形回帰のタイプ、すなわち計算すべきミスフィットのタイプを選択します。
  * **F** | **column_combination** :: [Type => Str]   $Arg = x|y|m|l|c$

    返される列の組み合わせを追加します。
  * **N** | **norm** :: [Type => Str | Int]          $Arg = 1|2|r|w$

    ミスフィット計算に使用するノルムを選択します。
  * **S** | **restrict** :: [Type => Str | []]        $Arg = [r]$

    出力されるレコードを制限します。
  * **T** | **equi_space** :: [Type => Str | List]     $Arg = [min/max/]inc[+a|n]] or file|list$

    引数によって示される等間隔の点で最適な回帰モデルを評価します。
  * **W** | **weighted** :: [Type => Str | []]     $Arg = [w][x][y][r]$

    重み付き回帰を指定し、どの重みが提供されるかを示します。
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    結果をJulia変数に返すのではなく、ASCIIファイルに保存します。ファイル名を引数として指定します。バイナリファイルとして保存するにはboオプションを使用します。
  * **append** :: [Type => Str]     $Arg = fname$

    結果を既存のファイル名$fname$に追加し、Julia変数に返すのではなく、バイナリファイルとして保存するにはboオプションを使用します。
  * **b** | **binary** :: [Type => Str]
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    ユーザーがコーディングした欠損データ値がGMTの公式NaN値にどのように変換されるかを制御します。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含むASCIIデータレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します（時間または地理データ）。
  * **g** | **gap** :: [Type => Str]           $Arg = [a]x|y|d|X|Y|D|[col]z[+|-]gap[u]$

    連続データポイント間の間隔を調べ、線の中にブレークを課します。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    主な入力ファイルにヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    主な入力の特定のデータ列を任意の順序で選択します。
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    主な出力の特定のデータ列を任意の順序で選択します。
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    入力レコードを周期的な座標に変換します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

```
