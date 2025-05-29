```
sample1d(cmd0::String="", arg1=nothing, kwargs...)
```

スプラインを使用して1次元テーブルデータを再サンプリングします

## パラメータ

  * **A** | **resample** :: [Type => Str]        $Arg = f|p|m|r|R$

    トラックの再サンプリング（-T…unitが設定されている場合）をどのように実行するかを選択できます。
  * **E** | **keeptext** :: [Type => Bool]

    入力データセットに末尾にテキストがあるレコードが含まれている場合、入力時刻と正確に一致する出力レコードにこれらを追加しようとします。
  * **F** | **interp** :: [Type => Str]   $Arg = l|a|c|n|s<p>[+1|+2]$

    l（線形）、a（アキマスプライン）、c（自然立方スプライン）、n（補間なし：最近接点）から選択します。[デフォルトはアキマ]。
  * **N** | **time_col** :: [Type => Int]      $Arg = t_col$

    独立変数（時間）を含む列を示します。最も左の列は#0、最も右の列は#(n_cols - 1)です。[デフォルトは0]。
  * **T** | **inc** | **range** :: [Type => List | Str]     $Arg = [min/max/]inc[+a|n]] or file|list$

    引数によって示される等間隔の点で最適フィット回帰モデルを評価します。
  * `cumdist` | `cumsum`: [Type => Bool]

    入力ラインに沿った累積距離を計算します。このためには、最初の2列が空間座標を含む必要があります。
  * `fill_nans` | `interp_nans`: [Type => Bool]

    すべてのNaNフィールドを隣接する値で補間された値に置き換えます。
  * `nonans`: [Type => Bool]

    NaNフィールドを持つすべての行を削除します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告をstderrに送信する冗長性レベルを選択します。
  * **W** | **weights** :: [Type => Int]     $Arg = w_col$

    スムージング立方スプラインで使用する重みの列番号を設定します。Fsが必要です。
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    結果をJulia変数に戻すのではなく、ASCIIファイルに保存します。ファイル名を引数として指定します。boオプションを使用してバイナリファイルとして保存します。
  * **append** :: [Type => Str]     $Arg = fname$

    結果を$fname$という既存のファイルに追加し、Julia変数に戻すのではなく、boオプションを使用してバイナリファイルとして保存します。
  * **b** | **binary** :: [Type => Str]
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    ユーザーがコーディングした欠損データ値がGMTの公式NaN値にどのように変換されるかを制御します。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含むASCIIデータレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します（時間または地理データ）。
  * **g** | **gap** :: [Type => Str]           $Arg = [a]x|y|d|X|Y|D|[col]z[+|-]gap[u]$

    連続データポイント間の間隔を調べて、ラインにブレークを課します。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    プライマリ入力の特定のデータ列を任意の順序で選択します。
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    プライマリ出力の特定のデータ列を任意の順序で選択します。
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    入力レコードを周期的な座標に変換します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

完全なドキュメントを見るには、次のように入力してください: $@? sample1d$
