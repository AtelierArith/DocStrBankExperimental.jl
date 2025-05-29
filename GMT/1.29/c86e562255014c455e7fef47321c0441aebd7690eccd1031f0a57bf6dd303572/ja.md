```
gmtsimplify(cmd0::String="", arg1=nothing; kwargs...)
```

ダグラス-ピーカーアルゴリズムを使用したラインの削減。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`gmtsimplify`](http://docs.generic-mapping-tools.org/latest/gmtsimplify.html)を参照してください。

## パラメータ

  * **T** | **tol** | **tolerance** :: [Type => Str | Number]    `Arg = tolerance[unit]`

    ユーザー単位での最大不一致許容値を指定します。データが直交座標でない場合は、距離単位を追加してください。   (http://docs.generic-mapping-tools.org/latest/gmtsimplify.html#t)
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告をstderrに送信する冗長性レベルを選択します。
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    結果をJulia変数に返すのではなく、ASCIIファイルに保存します。ファイル名を引数として指定してください。   boオプションを使用してバイナリファイルとして保存します。
  * **append** :: [Type => Str]     $Arg = fname$

    結果をJulia変数に返すのではなく、$fname$という既存のファイルに追加します。   boオプションを使用してバイナリファイルとして保存します。
  * **b** | **binary** :: [Type => Str]
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    ユーザーがコーディングした欠損データ値がGMTの公式NaN値にどのように変換されるかを制御します。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含むASCIIデータレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します（時間または地理データ）。
  * **g** | **gap** :: [Type => Str]           $Arg = [a]x|y|d|X|Y|D|[col]z[+|-]gap[u]$

    連続するデータポイント間の間隔を調べて、ラインにブレークを課します。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    プライマリ入力の特定のデータ列を任意の順序で選択します。
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    プライマリ出力の特定のデータ列を任意の順序で選択します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。
