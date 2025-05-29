```
gmtspectrum1d(cmd0::String="", arg1=nothing, kwargs...)
```

1次元の自己[および交差]スペクトルを1つ[または2つ]の時系列から計算します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`spectrum1d`](http://docs.generic-mapping-tools.org/latest/spectrum1d.html)を参照してください。

## パラメータ

  * **S** | **size** :: [Type => Str]        $Arg = segment_size$

    $$
    segment_size
    $$

    は、アンサンブル平均のためのウィンドウあたりのサンプル数の基数-2の数です。
  * **C** | **output** :: [Type => Str | []]        $Arg = [xycnpago]$

    入力の最初の2列を2つの時系列のサンプル、X(t)とY(t)として読み取ります。Y(t)を出力、X(t)をノイズのある線形システムの入力と見なします。
  * **D** | **sample_dist** :: [Type => Number]   $Arg = dt$

    時系列のサンプル間の間隔を設定します [デフォルト = 1]。
  * **L** | **leave_trend** :: [Type => Str | []]     $Arg = [h|m]$

    トレンドをそのままにします。デフォルトでは、変換前に線形トレンドが除去されます。
  * **N** | **name** :: [Type => Int]      $Arg = t_col$

    どれを示すか
  * **T** :: [Type => Bool]

    単一の合成結果ファイルをstdoutに書き込むのを無効にします。
  * **W** | **wavelength** :: [Type => Bool | Str]

    出力ファイルの列1に周波数の代わりに波長を書き込みます [デフォルト = 周波数、(サイクル / dt)]。
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

    入力および/または出力列のデータ型（時間または地理データ）を指定します。
  * **g** | **gap** :: [Type => Str]           $Arg = [a]x|y|d|X|Y|D|[col]z[+|-]gap[u]$

    連続データポイント間の間隔を調べて、線の中にブレークを課します。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    主な入力ファイルにはヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    主な入力の特定のデータ列を任意の順序で選択します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

完全なドキュメントを見るには、次のように入力します: $@? spectrum1d$
