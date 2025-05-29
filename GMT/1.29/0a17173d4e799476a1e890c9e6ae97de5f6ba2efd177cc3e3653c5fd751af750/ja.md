```
gmtsplit(cmd0::String="", arg1=nothing; kwargs...)
```

一連の (x,y[,z]) レコード [またはオプションで (x,y,z,d,h)] を読み込み、各系列が x,y 平面を通してほぼ一定の方位を持つように、これを (x,y[,z]) 系列の別々のリストに分割します。

完全な GMT ( `GMT.jl` ではなく) ドキュメントは [`gmtsplit`](http://docs.generic-mapping-tools.org/latest/gmtsplit.html) を参照してください。

## パラメータ

  * **A** | **azim_tol** :: [Type => Str | Array]  

    方位の見出しに対して +/- 許容度の度数内にあるセグメントのみを書き出します。北から時計回りに測定されます。[0 - 360]。
  * **C** | **course_change** :: [Type => Number]

    方位の変化が course_change 度を超えると、セグメントを終了します。
  * **D** | **min_dist** | **min_distance** :: [Type => Number]

    最小距離単位以上の長さでない限り、セグメントを書き出しません。
  * **F** | **filter** :: [Type => Str | Array]

    z 値および/または x,y 値をフィルタリングします。これらは d 座標の関数であると仮定します。xy*filter と z*filter は距離単位でのフィルタ幅です。
  * **N** | **multi** | **multifile** :: [Type => Bool | Str]

    各セグメントを別々の出力ファイルに書き出します。
  * **Q** | **fields** :: [Type => Str]

    xyzdh の任意の組み合わせを使用して、希望する出力を指定します。
  * **S** | **dh** | **dist_head** :: [Type => Bool]

    d と h の両方が提供されます。この場合、入力には x,y,z,d,h が含まれます。[デフォルトは (x,y,z) 入力を期待し、d,h は delta x, delta y から計算されます。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告を stderr に送信する冗長性レベルを選択します。
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    結果を Julia 変数に戻すのではなく、ASCII ファイルに保存します。ファイル名を引数として指定します。bo オプションを使用してバイナリファイルとして保存します。
  * **append** :: [Type => Str]     $Arg = fname$

    結果を既存のファイル名 $fname$ に追加し、Julia 変数に戻すのではなく、使用します。bo オプションを使用してバイナリファイルとして保存します。
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    主入力のネイティブバイナリ形式を選択します（副入力は常に ASCII です）。
  * **bo** | **binary_out** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    ネイティブバイナリ出力を選択します。
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    すべての入力列を調べ、任意の項目が nodata に等しい場合、この値を欠損データ項目として解釈し、NaN で置き換えます。
  * **do** | **nodata_out** :: [Type => Str or Number]     $Arg = nodata$

    すべての出力列を調べ、任意の項目が NAN に等しい場合、選択した欠損データ値で置き換えます。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含む ASCII データレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します（時間または地理データ）。
  * **g** | **gap** :: [Type => Str]           $Arg = [a]x|y|d|X|Y|D|[col]z[+|-]gap[u]$

    連続データポイント間の間隔を調べ、ラインにブレークを課すために使用します。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    主入力ファイルにヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    主入力の特定のデータ列を任意の順序で選択します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で 1 番目と 2 番目の列を入れ替えます。

完全なドキュメントを見るには、次のように入力してください: $@? splitxyz$ ```
